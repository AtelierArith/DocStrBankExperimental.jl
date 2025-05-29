```
frequencyspec(;ω_start::Real, ω_end::Real, logstep::Real= 0.05)
```

対数スケールで分布された周波数データのみを持つ `RheoFreqData` 構造体を生成します。

# 引数

  * `ω_start`: 最小周波数
  * `ω_end`: 最大周波数
  * `logstep`: 対数スケールでの周波数間のステップ、例: 0.1 → 10の値を1デシデンで。
