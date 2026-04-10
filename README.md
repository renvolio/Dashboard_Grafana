# Dashboard_Grafana
1) json Grafana dashboard with RED methodology and basic metrics with SLI, burn rate.
2) Also I show you alert rules based on Google SRE alerting best practices.
3) below I provide SLA and SLO my company.

SLO и SLA
 Наша компания предоставляет приложение для CRUD заметки. Ключевое бизнес действие на взгляд компании - это создание заметки. (по аналогии с "заказать" в приложениях по доставке еды).

—— Наши внутренние цели (SLO).

a) Availability (POST /notes, not 5xx): 95%
б) Latency (POST /notes < 1s): 95%
в) Latency (POST /notes < 5s): 99.95%
PS: slo должны быть с буфером, относительно sli, чтобы был запас бюджета.

——
Рассмотрим наш Error budget.

a) Availability (POST /notes): Доля риска =  5% в мес. Всего запросов  100000 в месяц. 5000 запросов может быть выделено на ошибку.

б) Latency (POST /notes < 1s): 
Доля риска = 5% в мес 
сколько запросов мы можем себе позволить дольше 1 секунды?
5000 запросов может быть медленнее 1 сек.

в) Latency (POST /notes < 5s): 
Доля риска = 0.05% в мес 
сколько запросов мы можем себе позволить дольше 5 секунд?
50 запроса может быть медленнее 5 сек. 

——
Предоставим SLA.

Гарантии SLA от нашей компании должны быть чуть мягче, чем SLO, чтобы иметь так называемый буфер в виде бюджета ошибок.

a) Availability (POST /notes, not 5xx): 94%

б) Latency (POST /notes < 1s): 94%

в) Latency (POST /notes < 5s): 99.9%
