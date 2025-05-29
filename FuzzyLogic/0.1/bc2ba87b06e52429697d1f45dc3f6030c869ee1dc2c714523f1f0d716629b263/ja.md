```julia
struct ConstantSugenoOutput{T<:Real} <: FuzzyLogic.AbstractSugenoOutputFunction
```

Sugeno推論システムにおける定数出力を表します。

  * `c::Real`: 定数出力の値。
