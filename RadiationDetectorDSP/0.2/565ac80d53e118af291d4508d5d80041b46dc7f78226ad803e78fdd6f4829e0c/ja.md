```
struct IntegratorCRFilter <: AbstractRadIIRFilter
```

修正されたCRフィルタ。フィルタには逆があります。

コンストラクタ:

  * `IntegratorCRFilter(fields...)`

フィールド:

  * `gain::Union{Real, Unitful.AbstractQuantity{<:Real}}`: フィルタゲイン
  * `cr::Union{Real, Unitful.AbstractQuantity{<:Real}}`: CR時定数
