```
struct IntegratorModCRFilter <: AbstractRadIIRFilter
```

修正されたCRフィルター。フィルターには逆があります。

コンストラクタ:

  * `IntegratorModCRFilter(fields...)`

フィールド:

  * `gain::Union{Real, Unitful.AbstractQuantity{<:Real}}`: フィルターゲイン
  * `cr::Union{Real, Unitful.AbstractQuantity{<:Real}}`: CR時定数
