```
struct CUSPChargeFilter <: AbstractRadFIRFilter
```

CUSPフィルター。

フィルターの定義とフィルター特性の議論については、以下を参照してください。

コンストラクタ:

  * `CUSPChargeFilter(; fields...)`

フィールド:

  * `sigma::Union{Real, Unitful.AbstractQuantity{<:Real}}`: 形状時間 (τₛ) の同等物。デフォルト: 450
  * `toplen::Union{Real, Unitful.AbstractQuantity{<:Real}}`: フラットトップ (FT) の長さ。デフォルト: 10
  * `tau::Union{Real, Unitful.AbstractQuantity{<:Real}}`: 指数の減衰定数。デフォルト: 20
  * `length::Union{Real, Unitful.AbstractQuantity{<:Real}}`: フィルターの総長 (L)。デフォルト: 100
  * `beta::AbstractFloat`: スケーリングファクター。デフォルト: 100.0
