# SPL LAB · Splunk 실습실

Splunk 검색 언어(SPL)를 브라우저에서 바로 연습하는 교육용 단일 HTML 페이지입니다.
`index.html` 파일 하나만 열면 동작하며 서버나 설치가 필요 없습니다.

## 여는 방법

- `index.html`을 더블클릭해 브라우저로 엽니다.
- 글꼴(Google Fonts)만 인터넷에서 불러오고, 오프라인이면 시스템 글꼴로 표시됩니다.

## 메뉴

| 메뉴 | 내용 |
| --- | --- |
| SPL 콘솔 | SPL을 입력하고 `Ctrl + Enter`로 실행. 이벤트 / 통계 / 시각화 탭, 필드 사이드바, 지원 명령어 도움말 |
| 장비 쿼리 | 방화벽 · 웹 서버 · 윈도우 · 리눅스별 필드 설명과 쿼리 템플릿 16개 |
| 실무 대시보드 | 보안 관제, 웹 서비스 대시보드 2종. 모든 KPI와 패널에 원본 SPL 표시 |
| 쿼리 연습장 | 초급·중급·고급 9문제. 결과를 정답 쿼리의 결과와 비교해 자동 채점 |
| 내 자료 | 저장한 쿼리, 실행 기록, 학습 노트 (브라우저 localStorage에 보관) |

## 간이 SPL 엔진

페이지 안의 JavaScript 엔진이 샘플 로그 위에서 SPL을 실행합니다.

- 검색 단계: `field=value`, `!=`, `>`, `>=`, 와일드카드 `*`, 따옴표 구문, `AND` / `OR` / `NOT`, 괄호, `earliest=-4h`
  (Splunk와 같이 검색 단계에서는 OR가 AND보다 먼저 계산됩니다)
- 명령어 19종: `search`, `where`, `eval`, `rex`, `fillnull`, `bin`(`bucket`), `stats`, `chart`, `timechart`, `top`, `rare`,
  `sort`, `head`, `tail`, `reverse`, `table`, `fields`, `rename`, `dedup`
- stats 함수: `count`, `dc`, `sum`, `avg`, `min`, `max`, `median`, `range`, `values`, `list`, `first`, `last`, `earliest`, `latest`
- eval 함수: `if`, `case`, `coalesce`, `round`, `floor`, `ceil`, `abs`, `lower`, `upper`, `len`, `substr`, `replace`,
  `like`, `match`, `cidrmatch`, `isnull`, `isnotnull`, `tonumber`, `tostring`, `strftime`, `now`, `min`, `max`

실제 Splunk의 모든 동작을 재현하지는 않으므로, 세부 결과는 실제 환경과 다를 수 있습니다.

## 샘플 데이터

2026-10-15 09:00 ~ 2026-10-16 09:00(KST) 24시간 분량, 약 2,700건의 가상 로그입니다. 시드가 고정되어 있어 매번 같은 데이터가 만들어집니다.

| index | sourcetype | 장비 |
| --- | --- | --- |
| firewall | fw:traffic | 방화벽 |
| web | access_combined | 웹 서버 |
| wineventlog | WinEventLog:Security | 윈도우 서버 |
| linux | linux_secure | 리눅스 서버 |

데이터에는 포트 스캔, 무차별 대입, 웹 취약점 스캐닝, 주문 API 장애 같은 사건이 숨어 있어 관제 실습에 쓸 수 있습니다.
외부 IP는 문서용 대역(RFC 5737)만 사용합니다.

## 참고

Splunk와 SPL은 해당 소유자의 상표이며, 이 페이지는 Splunk와 제휴 관계가 없습니다.
