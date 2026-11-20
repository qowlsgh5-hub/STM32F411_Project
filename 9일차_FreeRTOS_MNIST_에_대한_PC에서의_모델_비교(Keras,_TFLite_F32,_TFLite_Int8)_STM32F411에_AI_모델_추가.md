1. FreeRTOS
---

장점 자동으로 조정 잘해줌<br>
단점 비용, 메모리 스펙 등을 잘 못맞춰줘서 처음부터 다시 할 수도 있음<br>

# (1.2)CubeMX에서의 설정


## 1.2.1Middleware / NVIC / Clock
위의 것들은 
| 항목 | 최종 값 | 비고 |
|---|---|---|
| FREERTOS Interface | `CMSIS_V2` | `VP_FREERTOS_VS_CMSIS_V2.Mode=CMSIS_V2` |
| `configTOTAL_HEAP_SIZE` | `16384` | 태스크 3개 + 대기 여유 확보 |
| `configTICK_RATE_HZ` | 1000 | 1 ms tick |
| `configUSE_PREEMPTION` | enabled | 선점형 스케줄링 |
| `configUSE_MUTEXES` | enabled | `myMutex01` 사용 |
| `configLIBRARY_MAX_SYSCALL_INTERRUPT_PRIORITY` | 5 | EXTI 우선순위 5와 매칭 |
| NVIC Priority Group | `NVIC_PRIORITYGROUP_4` | "4 bits for pre-emption priority" |
| EXTI0 / EXTI15_10 우선순위 | 5 | `HAL_NVIC_SetPriority(..., 5, 0)` 생성됨 |
| SYS Timebase Source | **SysTick 유지** | 아래 참고 참고 |

순서대로 사진으로 표기
