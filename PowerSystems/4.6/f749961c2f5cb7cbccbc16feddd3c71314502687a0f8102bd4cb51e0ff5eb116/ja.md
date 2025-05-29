```
mutable struct RoundRotorQuadratic <: Machine
    base_machine::RoundRotorMachine
    saturation_coeffs::Tuple{Float64, Float64}
```

4状態のラウンドロータ同期機械で、二次飽和を持つ: IEEE Std 1110 §5.3.2 (モデル 2.2)。PSSEおよびPSLFのGENROUモデル。

# 引数

  * `base_machine::RoundRotorMachine`: ラウンドロータ機械モデル。
  * `saturation_coeffs::Tuple{Float64, Float64}``: 二次モデルの飽和係数。
