# 🛴 ATmega128을 사용한 안전한 전동 킥보드 시스템

**문제 정의**  
최소한의 안전 수칙을 지키지 않아 더 큰 사고로 이어지는 상황을 줄이기 위해, 안전 조건을 만족해야만 작동하는 킥보드 시스템을 구현했습니다.

**핵심 기능**
- 헬멧 착용 여부 확인
- 음주 수치 측정
- 양손 핸들링 확인
- 운행 시간 및 요금 계산
- 자동 조명 제어
- 헬멧부 ↔ 킥보드부 간 UART 통신

**시스템 구성**
- **헬멧부**
  - 스위치 센서를 이용한 헬멧 착용 여부 확인
  - MQ3 센서를 이용한 음주 수치 측정
  - 측정 데이터를 킥보드부로 전송
- **킥보드부**
  - 손잡이 양쪽 터치 센서를 이용한 양손 핸들링 확인
  - 운행 시간, 요금, 조명 제어
  - 주행 중에도 안전 조건을 지속적으로 검사
  - 조건 위반 시 운행 종료 후 요금 정산

**사용 기술**  
![ATmega128](https://img.shields.io/badge/ATmega128-5C3EE8?style=flat-square)
![MQ3](https://img.shields.io/badge/MQ3%20Alcohol%20Sensor-0A66C2?style=flat-square)
![Switch](https://img.shields.io/badge/Switch%20Sensor-2EA44F?style=flat-square)
![Touch](https://img.shields.io/badge/Touch%20Sensor-8250DF?style=flat-square)
![UART](https://img.shields.io/badge/UART%20Communication-6F42C1?style=flat-square)

**기여도**
- 헬멧 착용 여부 확인: 10/10
- 음주 수치 측정: 10/10
- 양손 핸들링 확인: 5/10
- UART 통신: 10/10

**문제 해결**
1. 머리카락 때문에 터치 센서가 정확히 동작하지 않는 문제가 있었습니다.  
   → 헬멧은 머리에 밀착 착용하는 것이 올바르다는 점을 반영해 스위치 센서로 지속 확인하도록 변경했습니다.
2. 헬멧부와 킥보드부 간 데이터 전송 시 여러 값을 개별 전송하면 지연이 발생했습니다.  
   → 알코올 수치와 헬멧 착용 여부 데이터를 하나로 통합하고 타이머 기반으로 전송해 지연을 줄였습니다.
