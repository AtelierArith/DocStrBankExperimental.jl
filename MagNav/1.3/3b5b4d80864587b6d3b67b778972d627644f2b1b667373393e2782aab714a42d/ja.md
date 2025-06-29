```
EKF_RT
```

リアルタイム (RT) 拡張カルマンフィルタ (EKF) 構造体、可変。

| **フィールド**  | **型**             | **説明**                                |
|:---------- |:----------------- |:------------------------------------- |
| `P`        | Matrix{`Float64`} | 非線形共分散行列                              |
| `Qd`       | Matrix{`Float64`} | 離散時間プロセス/システムノイズ行列                    |
| `R`        | Float64           | 測定（ホワイト）ノイズ分散                         |
| `baro_tau` | Float64           | バロメーター時定数 [s]                         |
| `acc_tau`  | Float64           | 加速度計時定数 [s]                           |
| `gyro_tau` | Float64           | ジャイロスコープ時定数 [s]                       |
| `fogm_tau` | Float64           | FOGM キャッチオール時定数 [s]                   |
| `date`     | Float64           | IGRF 用の測定日（小数年） [年]                   |
| `core`     | Bool              | true の場合、測定にコア磁場を含める                  |
| `nx`       | Int64             | 総状態次元                                 |
| `ny`       | Int64             | 測定次元                                  |
| `t`        | Float64           | 時間 [s]                                |
| `x`        | Vector{`Float64`} | フィルタリングされた状態、すなわち E(x*t   y*1,..,y_t) |
| `r`        | Vector{`Float64`} | 測定残差                                  |
