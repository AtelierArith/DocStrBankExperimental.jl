```
struct InvCRFilter <: AbstractRadIIRFilter
```

[`CRFilter`](@ref) の逆。

コンストラクタ:

  * `InvCRFilter(fields...)`

フィールド:

  * `cr::Union{Real, Unitful.AbstractQuantity{<:Real}}`: CR 時間定数
