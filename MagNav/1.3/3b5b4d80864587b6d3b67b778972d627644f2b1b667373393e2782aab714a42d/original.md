```
EKF_RT
```

Real-time (RT) extended Kalman filter (EKF) struct, mutable.

| **Field**  | **Type**          | **Description**                                     |
|:---------- |:----------------- |:--------------------------------------------------- |
| `P`        | Matrix{`Float64`} | non-linear covariance matrix                        |
| `Qd`       | Matrix{`Float64`} | discrete time process/system noise matrix           |
| `R`        | Float64           | measurement (white) noise variance                  |
| `baro_tau` | Float64           | barometer time constant [s]                         |
| `acc_tau`  | Float64           | accelerometer time constant [s]                     |
| `gyro_tau` | Float64           | gyroscope time constant [s]                         |
| `fogm_tau` | Float64           | FOGM catch-all time constant [s]                    |
| `date`     | Float64           | measurement date (decimal year) for IGRF [yr]       |
| `core`     | Bool              | if true, include core magnetic field in measurement |
| `nx`       | Int64             | total state dimension                               |
| `ny`       | Int64             | measurement dimension                               |
| `t`        | Float64           | time [s]                                            |
| `x`        | Vector{`Float64`} | filtered states, i.e., E(x*t   y*1,..,y_t)          |
| `r`        | Vector{`Float64`} | measurement residual                                |
