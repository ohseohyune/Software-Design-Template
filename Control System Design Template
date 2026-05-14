# Control System Design Template
> 제어 코드를 작성하기 전, 이 문서를 먼저 채운다.
> 수식은 LaTeX 표기를 따른다. 모든 변수는 차원과 단위를 명시한다.

---

## 📋 프로젝트 메타데이터

| 항목 | 내용 |
|---|---|
| 시스템명 | |
| 제어 목표 (한 줄) | |
| 작성일 | |
| 작성자 | |
| 버전 | v0.1 |

---

---

# PHASE 0 — 제어 문제 정의 (Problem Formulation)

---

## 0-1. 제어 목표 명세

**Primary Objective:**
```
(e.g., joint angle tracking with steady-state error < 0.01 rad)
```

**Secondary Objectives:**
```
(e.g., minimize control effort, reject torque disturbances)
```

**제어 성능 지표 (Specifications):**

| 지표 | 목표값 | 측정 방법 |
|---|---|---|
| Settling time (ts) | < ___ s | Step response, 2% criterion |
| Overshoot (Mp) | < ___ % | Step response |
| Steady-state error (ess) | < ___ | Step / ramp input |
| Rise time (tr) | < ___ s | 10%→90% |
| Bandwidth (ωbw) | > ___ rad/s | -3dB point of closed-loop |
| Phase margin (PM) | > ___ deg | Bode plot |
| Gain margin (GM) | > ___ dB | Bode plot |
| Disturbance rejection | ___ | 미정의 시 명시 |

---

## 0-2. 제어 대상 분류

**시스템 유형:**
- [ ] SISO / [ ] MIMO (입력 수: ___, 출력 수: ___)
- [ ] Linear / [ ] Nonlinear
- [ ] Continuous-time / [ ] Discrete-time / [ ] Hybrid
- [ ] Time-invariant / [ ] Time-varying
- [ ] Minimum phase / [ ] Non-minimum phase
- [ ] Stable open-loop / [ ] Unstable open-loop

**물리적 도메인:**
- [ ] 기계 (회전/병진)
- [ ] 전기/전자
- [ ] 열/유체
- [ ] 다중 도메인

---

## 0-3. 제약 조건

**액추에이터 제약:**
- 입력 범위: u ∈ [u_min, u_max] = [___, ___]  (단위: ___)
- 입력 변화율: |Δu/Δt| ≤ ___ (단위: ___)
- 슬루율 (Slew rate): ___ / s

**상태 제약:**
- x ∈ [x_min, x_max] (물리적/안전 한계)
- 구체적으로:

**센서 제약:**
- 측정 가능한 출력: y ∈ ℝ^p, p = ___
- 샘플링 주기: Ts = ___ s → fs = ___ Hz
- 측정 가능한 변수: (full state / output only)

**계산 제약:**
- 최대 제어 루프 주기: ___ ms
- 플랫폼: (MCU / CPU / GPU)
- 가용 메모리: ___

---

---

# PHASE 1 — 플랜트 모델링 (Plant Modeling)

---

## 1-1. 물리 모델 도출

**사용한 모델링 기법:**
- [ ] Newton-Euler
- [ ] Lagrangian (Euler-Lagrange)
- [ ] Bond graph
- [ ] System identification (데이터 기반)
- [ ] First principles + linearization

**가정 (Assumptions):**
- A1:
- A2:
- A3:
> ⚠️ 각 가정이 깨질 때 어떤 영향이 있는지 Phase 7에서 분석

---

## 1-2. 연속시간 상태공간 모델

**비선형 모델 (있는 경우):**

```
ẋ = f(x, u)
y  = h(x, u)

x ∈ ℝⁿ  (상태벡터, n = ___)
u ∈ ℝᵐ  (입력벡터, m = ___)
y ∈ ℝᵖ  (출력벡터, p = ___)
```

**상태 변수 정의:**

| 인덱스 | 변수 | 물리적 의미 | 단위 | 정상 범위 |
|---|---|---|---|---|
| x₁ | | | | |
| x₂ | | | | |
| xₙ | | | | |

**입력 변수 정의:**

| 인덱스 | 변수 | 물리적 의미 | 단위 | 범위 |
|---|---|---|---|---|
| u₁ | | | | |

**출력 변수 정의:**

| 인덱스 | 변수 | 물리적 의미 | 단위 |
|---|---|---|---|
| y₁ | | | |

---

## 1-3. 선형화 (Linearization)

**동작점 (Operating Point):**
```
x₀ = [  ]ᵀ
u₀ = [  ]ᵀ
y₀ = [  ]ᵀ
```

**선형 상태공간 모델:**
```
δẋ = A·δx + B·δu
δy  = C·δx + D·δu

δx = x - x₀,  δu = u - u₀
```

**시스템 행렬:**
```
A = (n×n)
    [ ... ]

B = (n×m)
    [ ... ]

C = (p×n)
    [ ... ]

D = (p×m)
    [ ... ]  (대부분 0)
```

**전달함수 (SISO인 경우):**
```
G(s) = C(sI - A)⁻¹B + D
     = (분자 다항식) / (분모 다항식)
     = ...
```

---

## 1-4. 파라미터 정의

| 파라미터 | 기호 | 값 | 단위 | 불확도 (±) | 출처 |
|---|---|---|---|---|---|
| | | | | | Datasheet / 측정 / 추정 |

---

## 1-5. 시스템 식별 (System Identification, 해당 시)

**실험 설계:**
- 입력 신호 유형: (PRBS / chirp / step / sine sweep)
- 주파수 범위: ___ ~ ___ Hz
- 데이터 길이: ___ s

**식별 방법:**
- [ ] ARX / ARMAX
- [ ] Subspace method (N4SID)
- [ ] Frequency domain fitting
- [ ] Neural network / data-driven

**검증 지표:**
- Fit (%): ___
- Residual analysis:

---

---

# PHASE 2 — 시스템 분석 (System Analysis)

---

## 2-1. 안정성 분석 (Open-loop)

**극점 (Poles):**

| 극점 | 위치 (s-plane) | 의미 |
|---|---|---|
| p₁ | | Stable / Unstable / Marginally stable |
| p₂ | | |

**불안정 극점 유무:**
- [ ] 없음 (open-loop stable)
- [ ] 있음 → 위치: ___ (반드시 closed-loop에서 안정화 필요)

**영점 (Zeros):**

| 영점 | 위치 | 비최소위상 여부 |
|---|---|---|
| z₁ | | [ ] RHP zero → 위상 여유 제한 주의 |

---

## 2-2. 제어 가능성 / 관측 가능성

**제어 가능성 (Controllability):**
```
C = [B, AB, A²B, ..., Aⁿ⁻¹B]
rank(C) = ___  (full rank = n이면 완전 제어 가능)
```
- [ ] 완전 제어 가능 (Fully Controllable)
- [ ] 부분 제어 불가능 → 불가능한 상태: ___

**관측 가능성 (Observability):**
```
O = [C; CA; CA²; ...; CAⁿ⁻¹]
rank(O) = ___  (full rank = n이면 완전 관측 가능)
```
- [ ] 완전 관측 가능 (Fully Observable)
- [ ] 부분 관측 불가능 → 관측 불가 상태: ___

> ⚠️ 제어 불가능한 모드가 불안정하면 안정화 불가능
> ⚠️ 관측 불가능한 모드가 불안정하면 추정기 설계 불가능

---

## 2-3. 주파수 영역 분석

**Bode Plot 특성:**
- DC gain:
- -3dB bandwidth:
- 위상 특성 (최소위상 여부):
- 공진 주파수 (있는 경우):

**RHP 제약이 성능에 미치는 영향:**
- RHP zero at s = z → bandwidth ≤ z/2 (rule of thumb)
- Time delay τ → PM 감소 ≈ ωcτ (rad)

---

## 2-4. 주요 시간 상수 분석

| 모드 | 시간 상수 (τ) | 고유 주파수 (ωn) | 감쇠비 (ζ) | 특성 |
|---|---|---|---|---|
| | | | | Fast / Slow / Dominant |

**지배 극점 (Dominant Poles):**
- 설계 목표 settling time ts → σ = 4/ts → desired Re(p) < -σ

---

---

# PHASE 3 — 제어기 설계 전략 (Controller Strategy)

---

## 3-1. 제어 구조 선택

**후보 구조 비교:**

| 구조 | 장점 | 단점 | 적합 조건 |
|---|---|---|---|
| PID | 직관적, 구현 단순 | MIMO 불가, 비선형 취약 | SISO, 약한 비선형 |
| State feedback (pole placement) | 전체 상태 배치 가능 | 풀 스테이트 측정 필요 | 상태 측정 가능 시 |
| LQR | 최적 트레이드오프 | 모델 정확도 의존 | 에너지 vs 성능 |
| LQG (LQR + Kalman) | 노이즈 환경에서 최적 | 설계 복잡도 | 센서 노이즈 존재 시 |
| MPC | 제약 처리, 예측 | 계산 비용 | 제약 있는 MIMO |
| Sliding Mode | 강건, 불확실성 처리 | 채터링 | 강한 불확실성 |
| Feedback Linearization | 비선형 정확 보상 | 모델 정확도 의존 | 정확한 모델 있을 때 |
| H∞ | 강건 안정성 보장 | 설계 복잡도 | 불확실성 범위 알 때 |

**최종 선택:**
> 선택한 구조:
> 이유:
> 포기한 대안과 이유:

---

## 3-2. 제어 루프 구조도

```
참조입력 r(t)      오차 e(t)                제어입력 u(t)       상태/출력
    ──────→ [+] ──────→ [ Controller ] ──────→ [ Plant ] ──────→
             ↑- - - - - - - - - - - - - - - - - -↓
                           피드백 y(t)
                      [ Observer / Estimator ]  (필요 시)
                      [ Disturbance Observer ]  (필요 시)
                      [ Feedforward ]           (필요 시)
```

**구성 요소 체크:**
- [ ] Feedback controller
- [ ] Feedforward / Reference model
- [ ] State observer / Estimator (Luenberger / Kalman)
- [ ] Disturbance observer (DOB)
- [ ] Anti-windup
- [ ] Reference pre-filter / pre-compensator
- [ ] Gain scheduling

---

## 3-3. 분리 원리 적용 여부 (Separation Principle)

> LTI 시스템에서 상태 피드백과 추정기를 독립적으로 설계 가능

- [ ] 적용 가능 (LTI, 시스템이 controllable + observable)
- [ ] 적용 불가 (비선형 / 시변) → 결합 설계 필요

---

---

# PHASE 4 — 제어기 설계 (Controller Design)

---

## 4-1. 제어기 수학적 설계

### 4-1-A. [선택한 제어기 이름] 설계

**설계 파라미터:**

```
(설계 과정의 수식 전개)

예: LQR이면
  minimize J = ∫(xᵀQx + uᵀRu)dt

  Q = diag([q₁, q₂, ..., qₙ])  선택 근거:
  R = diag([r₁, ..., rₘ])      선택 근거:

  → Riccati equation: AᵀP + PA - PBR⁻¹BᵀP + Q = 0
  → K = R⁻¹BᵀP
  → u = -Kx
```

**설계 결과:**
```
Controller gain / parameters:
K = [   ]  (또는 전달함수, 상태공간 등)
```

**폐루프 극점 위치:**

| 극점 | 위치 | 감쇠비 ζ | 고유 주파수 ωn |
|---|---|---|---|
| | | | |

**안정성 여유:**
- Phase Margin:    ___ deg  (목표: > ___ deg)
- Gain Margin:     ___ dB   (목표: > ___ dB)
- Delay Margin:    ___ ms

---

### 4-1-B. 상태 추정기 설계 (Observer / Kalman Filter, 해당 시)

**추정기 유형:**
- [ ] Luenberger Observer
- [ ] Kalman Filter (LKF)
- [ ] Extended Kalman Filter (EKF)
- [ ] Unscented Kalman Filter (UKF)

**Luenberger Observer:**
```
x̂̇ = Ax̂ + Bu + L(y - Cx̂)

관측기 극점 배치 (제어기 극점보다 2~5배 빠르게):
desired observer poles: ___
L = [   ]
```

**Kalman Filter:**
```
프로세스 노이즈 공분산:  Q_kf = diag([___])
측정 노이즈 공분산:      R_kf = diag([___])

Q_kf 선택 근거: (모델 불확실성 크기 기반)
R_kf 선택 근거: (센서 스펙 / 실험적 측정)
```

**EKF Jacobian (해당 시):**
```
F = ∂f/∂x |_(x̂,u)
H = ∂h/∂x |_(x̂)
```

---

### 4-1-C. Feedforward 설계 (해당 시)

```
목적: 참조 추적 성능 향상, 과도응답 개선

u_ff = [설계 수식]
```

---

### 4-1-D. Disturbance Observer (DOB, 해당 시)

```
목적: 모델 불확실성 및 외란을 추정하여 보상

Q-filter 설계:
Q(s) = ...  (안정성 조건: 상대차수 ≥ 0)

Bandwidth of DOB: ω_dob = ___ rad/s
```

---

## 4-2. 게인 스케줄링 (해당 시)

**스케줄링 변수:**
```
ρ(t) ∈ [ρ_min, ρ_max]  (e.g., 속도, 온도, 페이로드)
```

**동작점 목록:**

| 동작점 | ρ 값 | A(ρ), B(ρ) | Controller gain K(ρ) |
|---|---|---|---|
| OP-1 | | | |
| OP-2 | | | |

**보간 방법:**
- [ ] Linear interpolation
- [ ] LPV (Linear Parameter Varying)
- [ ] Fuzzy / lookup table

**전환 조건 및 범프리스 전환 (Bumpless Transfer):**
```
전환 트리거:
bump 방지 방법:
```

---

---

# PHASE 5 — 이산화 (Discretization)

> 연속시간 설계 → 디지털 구현 변환

---

## 5-1. 샘플링 주기 결정

**Nyquist 기준:**
```
fs ≥ 2 × ω_bw (최소), 실용적으로 fs ≥ 10~20 × ω_bw

제어 대역폭: ω_bw = ___ rad/s  →  f_bw = ___ Hz
권장 fs: ___ Hz  →  Ts = ___ ms
```

**선택한 샘플링 주기:**
```
Ts = ___ ms  (fs = ___ Hz)
선택 이유:
```

**샘플링 지연 영향:**
```
등가 시간 지연: τ_delay ≈ Ts/2
PM 감소량: Δφ ≈ ω_c × Ts/2 × (180/π) deg
```

---

## 5-2. 이산화 방법 선택

| 방법 | 수식 | 특성 | 적합 상황 |
|---|---|---|---|
| ZOH | exact hold | 계단 입력에 정확 | 플랜트 이산화 |
| Tustin (Bilinear) | s=(2/Ts)(z-1)/(z+1) | 주파수 특성 보존 | 제어기 이산화 |
| Tustin + prewarping | ωd = (2/Ts)tan(ωTs/2) | 특정 주파수 정확 | 공진 주파수 중요 시 |
| Forward Euler | s=(z-1)/Ts | 단순, 불안정 위험 | 사용 지양 |
| Backward Euler | s=z(z-1)/Ts | 안정적, 위상 지연 | 느린 시스템 |

**선택한 방법:**
```
플랜트 이산화: ZOH (Ts = ___ ms)
제어기 이산화: Tustin (prewarping at ω = ___ rad/s)
```

---

## 5-3. 이산 시스템 모델

```
x[k+1] = Ad·x[k] + Bd·u[k]
y[k]   = Cd·x[k] + Dd·u[k]

Ad = (n×n) = ...
Bd = (n×m) = ...
Cd = (p×n) = ...
```

**이산화 후 안정성 재확인:**
```
Ad의 고유값 (모두 단위원 내부에 있어야 함):
λ₁ = ___, |λ₁| = ___
λ₂ = ___, |λ₂| = ___
```

---

## 5-4. 이산 제어기 차분방정식

```
(구현할 실제 점화식)

예: PID
u[k] = u[k-1] + Kp(e[k] - e[k-1])
               + Ki·Ts·e[k]
               + Kd/Ts·(e[k] - 2e[k-1] + e[k-2])
```

---

---

# PHASE 6 — 구현 설계 (Implementation Design)

---

## 6-1. 소프트웨어 구조

**제어 루프 구조:**

```
┌─────────────────────────────────────────────┐
│                Control Loop                  │  주기: ___ ms
│                                             │
│  1. Sensor Read          → raw measurement  │
│  2. Signal Processing    → filtered y[k]    │
│  3. State Estimation     → x̂[k]            │
│  4. Reference Generation → r[k]             │
│  5. Error Computation    → e[k] = r[k]-y[k] │
│  6. Controller Update    → u[k]             │
│  7. Saturation / Limit   → u_sat[k]         │
│  8. Anti-windup Update                      │
│  9. Actuator Write       → command          │
│  10. Logging / Monitor                      │
└─────────────────────────────────────────────┘
```

---

## 6-2. 핵심 모듈 정의

| 모듈 | 책임 | 입력 | 출력 |
|---|---|---|---|
| SensorInterface | 센서 읽기 및 단위 변환 | raw ADC/encoder | SI 단위 측정값 |
| SignalProcessor | 필터링, 이상값 제거 | raw y | filtered y |
| StateEstimator | 상태 추정 | y, u | x̂ |
| ReferenceGenerator | 목표값 생성/보간 | command | r[k] |
| Controller | 제어 입력 계산 | e, x̂ | u |
| ActuatorInterface | 명령 변환 및 전송 | u (SI) | PWM/CAN/etc |
| SafetyMonitor | 한계 감시 및 차단 | x̂, u | enable/disable |
| DataLogger | 데이터 기록 | all signals | log file |

---

## 6-3. 필터 설계

**센서 노이즈 특성:**
```
측정 노이즈 표준편차: σ_noise = ___  (단위: ___)
노이즈 주파수 범위: ___ Hz 이상
```

**필터 유형 선택:**

| 필터 | 전달함수 / 수식 | 차단 주파수 | 적용 신호 |
|---|---|---|---|
| 1차 LPF | H(s) = ωc/(s+ωc) | ωc = ___ rad/s | |
| 2차 Butterworth | | | |
| Moving Average | | | |
| Derivative filter | N/(s/N+1) | N = ___ | 미분 항 |

**필터 파라미터:**
```
cutoff frequency: ωc = ___ rad/s (signal BW의 ___ 배)
이산화 (Tustin):
  α = Ts·ωc / (2 + Ts·ωc)
  y_f[k] = α·y[k] + α·y[k-1] + (1-2α)·y_f[k-1]
```

---

## 6-4. Anti-windup 설계

**Windup 발생 조건:**
```
적분기 포화 조건: |u_unsat| > u_max 일 때
```

**Anti-windup 방법:**

| 방법 | 수식 | 특성 |
|---|---|---|
| Clamping | integrator 정지 조건 | 단순 |
| Back-calculation | u_i += Kt(u_sat - u_unsat) | 부드러운 복귀 |
| Conditional integration | 오차 방향 조건 | 직관적 |

**선택 및 파라미터:**
```
방법: Back-calculation
Kt = 1/Ti  (또는 별도 튜닝)
```

---

## 6-5. 모드 전환 / Bumpless Transfer

**제어 모드 정의:**

| 모드 | 설명 | 진입 조건 | 탈출 조건 |
|---|---|---|---|
| IDLE | 초기화 완료, 대기 | 시작 시 | Enable 신호 |
| MANUAL | 수동 제어 | 수동 명령 | Auto 신호 |
| AUTO | 자동 제어 | Auto 신호 | Manual / Fault |
| FAULT | 안전 정지 | 임계 초과 | Reset |

**상태 전환 다이어그램:**
```
IDLE ──enable──> AUTO ──manual──> MANUAL
                  ↓ fault           ↓ fault
                FAULT <───────────FAULT
```

**Bumpless Transfer 조건:**
```
모드 전환 시 u의 불연속 방지:
  AUTO → MANUAL: u_manual = u_auto (초기값 동기화)
  MANUAL → AUTO: integrator = u_manual - u_p (적분기 초기화)
```

---

## 6-6. 안전 모니터 (Safety Monitor)

| 감시 항목 | 임계값 | 경고 조건 | 차단 조건 | 복구 방법 |
|---|---|---|---|---|
| 상태 범위 | x ∈ [___, ___] | 90% | 100% | Reset |
| 제어 입력 | u ∈ [___, ___] | Saturation | Hard limit | Clamp |
| 센서 이상 | | Spike detect | Timeout | Fallback |
| 루프 타이밍 | Ts ± ___% | Jitter > ___ | Miss > ___ | Emergency stop |

---

## 6-7. 코드 인터페이스 (Stub)

```python
class Controller:
    def __init__(self, params: ControllerParams) -> None:
        """
        파라미터 초기화, 내부 상태 초기화
        """
        ...

    def reset(self) -> None:
        """
        적분기, 이전값, 추정기 상태를 초기값으로 리셋
        """
        ...

    def update(self,
               y: np.ndarray,     # 측정값, shape (p,)
               r: np.ndarray,     # 참조값, shape (p,)
               dt: float          # 실제 샘플링 간격 [s]
               ) -> np.ndarray:   # 제어 입력, shape (m,)
        """
        한 스텝 제어 계산.

        Args:
            y:  측정 출력값
            r:  참조 입력값
            dt: 실제 경과 시간 (nominal Ts와 비교용)

        Returns:
            u: 포화 처리된 제어 입력
        """
        ...

    def get_state(self) -> ControllerState:
        """
        현재 내부 상태 반환 (로깅/모니터링용)
        """
        ...
```

---

## 6-8. ROS2 구현 구조 (해당 시)

**노드 구성:**

| 노드 | 책임 | 실행 방식 |
|---|---|---|
| `sensor_node` | 센서 드라이버 | Timer callback, ___ Hz |
| `estimator_node` | 상태 추정 | Subscriber callback |
| `controller_node` | 제어 계산 | Timer callback, ___ Hz |
| `actuator_node` | 액추에이터 드라이버 | Subscriber callback |
| `monitor_node` | 상태 모니터링 | Timer callback, ___ Hz |

**토픽 설계:**

| 토픽 | 타입 | Publisher | Subscriber | QoS | Hz |
|---|---|---|---|---|---|
| `/sensor/raw` | | sensor_node | estimator_node | BestEffort, depth=1 | |
| `/state/estimated` | | estimator_node | controller_node | Reliable, depth=1 | |
| `/control/cmd` | | controller_node | actuator_node | Reliable, depth=1 | |
| `/control/status` | | controller_node | monitor_node | BestEffort, depth=10 | |

**QoS 선택 기준:**
```
실시간 제어 토픽: BestEffort, keep_last=1  (최신값만 중요)
명령 토픽:        Reliable, keep_last=1    (손실 불가)
로그/모니터:      BestEffort, keep_last=10
```

**타이밍 구조:**
```
Timer(Ts_control) ──triggers──> controller callback
                                    ↓
                            read latest sensor data  (non-blocking)
                                    ↓
                            compute u[k]
                                    ↓
                            publish cmd
```

---

---

# PHASE 7 — 파라미터 튜닝 전략 (Tuning Strategy)

---

## 7-1. 튜닝 파라미터 목록

| 파라미터 | 초기값 | 튜닝 범위 | 영향 |
|---|---|---|---|
| | | | |

---

## 7-2. 튜닝 순서 및 방법

```
Step 1: 플랜트 모델 검증
  → open-loop step response 측정
  → 모델 예측과 실제 비교 (fit %)

Step 2: 추정기 튜닝 (먼저)
  → Q_kf 증가: 모델 불신, 측정 신뢰
  → R_kf 증가: 측정 불신, 모델 신뢰
  → 추정값과 실제 비교

Step 3: 제어기 튜닝
  → 가장 보수적인 게인부터 시작
  → 안정성 여유 확인하며 점진적 증가
  → 성능 지표 달성 여부 확인

Step 4: 강건성 확인
  → 모델 파라미터 ±20% 변동 시 성능 확인
  → 외란 주입 테스트
```

---

## 7-3. 튜닝 기준 (각 제어기별)

**PID 튜닝 가이드라인:**
```
Kp: bandwidth에 영향. 증가 → 빠른 응답, 진동 위험
Ki: 정상상태 오차 제거. 증가 → 느린 적분, windup 위험
Kd: 감쇠. 증가 → 노이즈 증폭 위험 → derivative filter 필수

Ziegler-Nichols (초기값용, 정밀 튜닝 아님):
  Ku (ultimate gain), Tu (period) 측정 후 표 참조
```

**LQR Q, R 튜닝 가이드라인:**
```
Bryson's rule (출발점):
  Q_ii = 1 / (x_i,max)²
  R_jj = 1 / (u_j,max)²

Q 증가 → 해당 상태 더 강하게 규제 → 빠른 응답, 큰 입력
R 증가 → 입력 사용 억제 → 느린 응답, 작은 입력
```

**Kalman Filter 튜닝 가이드라인:**
```
R_kf: 센서 스펙에서 직접 측정 가능
Q_kf: 모델 오차 크기로 추정, 실험적으로 확인

Q/R ratio:
  비율 크게 → 측정값 더 신뢰 → 빠른 추적, 노이즈 민감
  비율 작게 → 모델 더 신뢰 → 부드러운 추정, 느린 추적
```

---

---

# PHASE 8 — 안정성 증명 / 검증 (Stability & Verification)

---

## 8-1. 이론적 안정성 분석

**폐루프 극점 위치 (설계 후):**
```
모두 s-plane 좌반면 / z-plane 단위원 내부에 있는가:
[ ] 연속시간: Re(λᵢ) < 0  for all i
[ ] 이산시간: |λᵢ| < 1    for all i
```

**Lyapunov 안정성 (비선형 / 강건성 분석 시):**
```
후보 Lyapunov 함수: V(x) = xᵀPx  (또는 물리적 에너지 함수)

V(x) > 0  ∀x ≠ 0:  [ ] 확인
V̇(x) < 0  ∀x ≠ 0:  [ ] 확인

V̇ = xᵀ(AᵀP + PA)x < 0
→ AᵀP + PA = -Q  (Q > 0 이면 성립)
```

**강건 안정성 여유:**
```
파라미터 불확실성 범위: ΔP ∈ [___%, ___% of nominal]
최악 조건에서의 PM: ___ deg
최악 조건에서의 GM: ___ dB
```

---

## 8-2. 시뮬레이션 검증 계획

**시뮬레이션 환경:**
- [ ] Python (scipy.integrate.solve_ivp)
- [ ] MATLAB/Simulink
- [ ] Gazebo
- [ ] MuJoCo
- [ ] PyBullet

**테스트 케이스:**

| ID | 테스트 | 입력 | 합격 기준 |
|---|---|---|---|
| T-01 | Step response | r = 단위 계단 | ts < ___, Mp < ___ |
| T-02 | Ramp tracking | r = 경사 | ess < ___ |
| T-03 | Disturbance rejection | d = 단위 계단 | 복귀 시간 < ___ |
| T-04 | 파라미터 변동 | P ±20% | 안정 유지 |
| T-05 | 입력 포화 | 대형 step | Windup 없음 |
| T-06 | 센서 노이즈 | σ = ___ | u 분산 < ___ |
| T-07 | 초기 조건 | x₀ ≠ 0 | 수렴 |

---

## 8-3. 하드웨어 인-더-루프 (HIL) 계획

**HIL 환경:**
```
실제 제어기 코드 → [Hardware] → 시뮬레이션된 플랜트 모델
```

**HIL 단계:**
```
1. SIL (Software-in-the-Loop): 전체 소프트웨어 시뮬레이션
2. PIL (Processor-in-the-Loop): 타겟 MCU + 시뮬레이션 플랜트
3. HIL: 실제 센서/액추에이터 + 시뮬레이션 플랜트
4. 실제 실험
```

---

## 8-4. 실험 검증 절차

```
Step 1: 저게인으로 open-loop 응답 확인
Step 2: 최소 게인으로 closed-loop 안정성 확인
Step 3: 점진적 게인 증가 + 안정성 여유 모니터링
Step 4: 성능 지표 달성 확인
Step 5: 강건성 테스트 (페이로드 변화, 외란 인가)
Step 6: 장시간 실행 안정성 확인
```

**비상 정지 조건 (사전 설정 필수):**
```
|x| > x_emergency: 즉시 제어 차단
|u| > u_hardware_limit: 즉시 제어 차단
sensor timeout > ___ ms: 안전 모드
```

---

---

# PHASE 9 — 실패 모드 분석 (Failure Mode Analysis)

---

## 9-1. 모델 불확실성 영향

| 불확실 파라미터 | 공칭값 | 실제 범위 | 영향 | 허용 범위 |
|---|---|---|---|---|
| | | ±___% | 안정성 / 성능 | |

**모델-실제 불일치 (Model-Reality Mismatch):**
- 미모델 동역학: (고주파 모드, 유연성, 마찰)
- 비선형성: (데드존, 백래시, 포화)
- 시변 특성: (온도, 마모, 페이로드)

---

## 9-2. 제어기 고유 실패 모드

| 실패 모드 | 발생 조건 | 증상 | 방지 방법 |
|---|---|---|---|
| Integrator windup | 포화 중 적분 지속 | 큰 오버슈트, 느린 복귀 | Anti-windup |
| Derivative kick | 참조 급변 시 | 입력 스파이크 | D-on-measurement |
| Sensor dropout | 센서 통신 실패 | 잘못된 추정, 발산 | Timeout + fallback |
| Sampling jitter | 비균등 샘플링 | 성능 저하 | 실제 dt 사용 |
| Observer divergence | Q/R 잘못 설정 | 추정 발산 | 공분산 바운딩 |
| Noise amplification | 높은 Kd | 액추에이터 마모 | Derivative filter |
| Parameter drift | 시간에 따른 변화 | 성능 저하 | 적응 제어 / 재튜닝 |

---

## 9-3. 하드웨어 인터페이스 실패

| 실패 | 감지 방법 | 대응 |
|---|---|---|
| 센서 단락/단선 | 범위 초과 감지 | 마지막 유효값 유지 + 경고 |
| 액추에이터 포화 | 명령 ≠ 피드백 | Anti-windup 활성화 |
| 통신 지연 | timestamp 확인 | 예측값 사용 또는 정지 |
| 전원 이상 | 전압 모니터링 | 안전 위치로 이동 |

---

---

# 설계 검토 체크리스트 (Control Design Review)

## 모델링
- [ ] 모든 가정이 명시되었고, 각 가정의 유효 범위가 정의되었는가
- [ ] 파라미터 출처(측정/추정/datasheet)가 기록되었는가
- [ ] 단위와 좌표계가 일관되게 사용되었는가

## 분석
- [ ] 제어 가능성 행렬의 rank가 확인되었는가
- [ ] 관측 가능성 행렬의 rank가 확인되었는가
- [ ] RHP 극점/영점이 식별되었고 설계에 반영되었는가
- [ ] 샘플링 주파수가 대역폭의 10배 이상인가

## 제어기 설계
- [ ] 폐루프 극점이 모두 안정 영역에 있는가
- [ ] Phase Margin > 30deg, Gain Margin > 6dB 이상인가
- [ ] 입력 포화 시 Anti-windup이 동작하는가
- [ ] 이산화 방법과 샘플링 시간이 명시되었는가

## 구현
- [ ] 제어 루프의 실행 순서가 명확히 정의되었는가
- [ ] 모든 상태 변수의 초기화 조건이 정의되었는가
- [ ] Bumpless transfer 조건이 설계되었는가
- [ ] 안전 모니터와 비상 정지 조건이 구현되었는가

## 검증
- [ ] 시뮬레이션에서 모든 테스트 케이스를 통과하였는가
- [ ] 파라미터 ±20% 변동에서도 안정적인가
- [ ] 실험 전 비상 정지 조건이 설정되었는가

---

---

# 변경 이력 (Change Log)

| 날짜 | 버전 | 변경 내용 | 작성자 |
|---|---|---|---|
| | v0.1 | 초안 작성 | |
