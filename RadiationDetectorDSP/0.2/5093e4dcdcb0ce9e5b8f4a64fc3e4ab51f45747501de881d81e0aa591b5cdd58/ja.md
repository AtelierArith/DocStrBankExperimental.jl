```
struct InvModCRFilter <: AbstractRadIIRFilter
```

[`ModCRFilter`](@ref) の逆数。

コンストラクタ:

  * `InvModCRFilter(fields...)`

フィールド:

  * `cr::Union{Real, Unitful.AbstractQuantity{<:Real}}`: CR 時間定数
