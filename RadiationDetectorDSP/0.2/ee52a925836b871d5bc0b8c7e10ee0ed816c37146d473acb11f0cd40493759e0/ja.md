```
struct IntegratorFilter <: AbstractRadIIRFilter
```

インテグレータフィルタ。逆は [`DifferentiatorFilter`](@ref) です。

コンストラクタ:

  * `IntegratorFilter(fields...)`

フィールド:

  * `gain::Union{Real, Unitful.AbstractQuantity{<:Real}}`: フィルタゲイン
