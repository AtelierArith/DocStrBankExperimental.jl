```
mutable struct RoundRotorExponential <: Machine
    base_machine::RoundRotorMachine
    saturation_coeffs::Tuple{Float64, Float64}
```

指数飽和を持つ4状態ラウンドロータ同期機械：IEEE Std 1110 §5.3.2 (モデル 2.2)。PSSEおよびPSLFのGENROEモデル。

# 引数

  * `base_machine::RoundRotorMachine`: ラウンドロータ機械モデル。
  * `saturation_coeffs::Tuple{Float64, Float64}``: 指数モデルの飽和係数。
