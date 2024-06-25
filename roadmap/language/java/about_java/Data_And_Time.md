# 자바의 날짜와 시간 API

- java.time.LocalDate : 시간대를 고려하지 않고 날짜만 표현한다.'
```
LocalDate today = LocalDate.now();
System.out.println(today); // 예: 2024-06-25
```
- java.time.LocalTime : 시간데 없이 시간만 보여준다.
```
LocalTime now = LocalTime.now();
System.out.println(now); // 예: 12:34:56.789
```
- java.time.LocalDateTime : 날짜와 시간을 모두 포함하지만 시간대 정보는 없다.
```
LocalDateTime dateTime = LocalDateTime.now();
System.out.println(dateTime); // 예: 2024-06-25T12:34:56.789
```
- java.time.ZonedDateTime : 날짜 + 시간 + 시간대
```
ZonedDateTime zonedDateTime = ZonedDateTime.now();
System.out.println(zonedDateTime); // 예: 2024-06-25T12:34:56.789+09:00[Asia/Seoul]
```
- java.time.OffsetTime : UTC/GMT 오프셋을 사용해 시간만
```
OffsetTime offsetTime = OffsetTime.now();
System.out.println(offsetTime); // 예: 12:34:56.789+09:00
```
- java.time.Clock : 특정 시간대에 현재 순간 제공
```
Clock clock = Clock.system(ZoneId.of("Asia/Seoul"));
System.out.println(clock.instant()); // 예: 2024-06-25T03:34:56.789Z
```
- java.time.Instant : UTC를 기준으로 한 타임 스탬프를 제공
```
Instant instant = Instant.now();
System.out.println(instant); // 예: 2024-06-25T03:34:56.789Z
```
- java.time.Duration : 두 시간 사이의 지속 기간을 초나 나노초 단위로 표현
```
Duration duration = Duration.between(LocalTime.NOON, LocalTime.MIDNIGHT);
System.out.println(duration.getSeconds()); // 예: 43200
```
- java.time.Period : 두 날짜 사이의 기간을 연, 월, 일 단위로 표현
```
Period period = Period.between(LocalDate.of(2024, 1, 1), LocalDate.of(2024, 12, 31));
System.out.println(period); // 예: P11M30D
```
- java.time.ZoneOffset : UTC로부터 시간대 오프셋을 나타냄
```
ZoneOffset zoneOffset = ZoneOffset.ofHours(9);
System.out.println(zoneOffset); // 예: +09:00
```


  
---
### ?
- UTC(협정 세계시)  
Coordinated Universal Time의 약자로 현정 세꼐시를 의미한다. UTC는 국제적으로 표준화된 시간 체계로,
전세계적으로 시간의 기준점 역할을 한다. UTC는 그리니티 평균시 GMT와 기술적으로 동일한 시간을 나타내지만,
UTC가 좀 더 정확한 원자 시계를 기반으로 조덩되어있다. 원자시계는 지구 자전 속도 변화에 영향을 받지 않으므로, 
UTC는 국제적인 과학과 통신에 매우 중요한 기준 시간으로 사용된다.

- 시간과 시간대의 차이?????
1. 시간 : 특정 순간을 지칭하는 말로 보통 시, 분, 초 단위로 표현됨.
2. 시간대 : 지구를 가로지르는 가상의 세로 줄로 나눈 구역으로 각 구역은 표준 시간을 갖는다. 
시간대는 기본적으로 UTC와의 시간 차이로 결정되며 이를 통해 지역별로 표준 시간을 설정한다.  

=> 차이점 : UTC는 시간대와 무관하게 일정한 기준 시간을 제공하는 반면 시간대는 지리적 위체에 따라 다르며, 
같은 시간대 내에서도 국가별로 일광 절약 시간제의 적용 여부에 따라 시간이 달라질 수 있다. 