```
mutable struct SalientPoleExponential <: Machine
    base_machine::SalientPoleMachine
    saturation_coeffs::Tuple{Float64, Float64}
```

3状態のサリエントポール同期機械で、指数飽和を持つ: IEEE Std 1110 §5.3.2 (モデル 2.1)。PSSEおよびPSLFのGENSAE。

# 引数:

  * `base_machine::SalientPoleMachine`: サリエントポール機械モデル。
  * `saturation_coeffs::Tuple{Float64, Float64}``: 指数モデルの飽和係数。
