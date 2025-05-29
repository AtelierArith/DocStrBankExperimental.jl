```julia
mutable struct MFourMomentum <: QEDbase.AbstractFourMomentum
```

粒子または場の四運動量を静的にモデル化するために使用される実成分を持つ可変ローレンツベクトルを構築します。

# フィールド

  * `E::Float64`: エネルギー成分
  * `px::Float64`: `x` 成分
  * `py::Float64`: `y` 成分
  * `pz::Float64`: `z` 成分
