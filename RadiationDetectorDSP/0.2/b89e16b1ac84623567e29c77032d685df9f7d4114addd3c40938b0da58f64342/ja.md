```
struct DifferentiatorFilter <: AbstractRadIIRFilter
```

積分器フィルタです。その逆は [`IntegratorFilter`](@ref) です。

コンストラクタ:

  * `DifferentiatorFilter(fields...)`

フィールド:

  * `gain::Union{Real, Unitful.AbstractQuantity{<:Real}}`: フィルタゲイン
