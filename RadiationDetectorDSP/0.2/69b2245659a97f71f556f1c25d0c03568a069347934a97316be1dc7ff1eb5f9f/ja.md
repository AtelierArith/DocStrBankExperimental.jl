```
struct InvRCFilter <: AbstractRadIIRFilter
```

[`RCFilter`](@ref) の逆。

コンストラクタ:

  * `InvRCFilter(fields...)`

フィールド:

  * `rc::Union{Real, Unitful.AbstractQuantity{<:Real}}`: RC 時間定数
