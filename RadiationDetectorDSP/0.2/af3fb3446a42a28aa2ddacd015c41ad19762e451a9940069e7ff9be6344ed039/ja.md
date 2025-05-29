```
struct ZACChargeFilter <: AbstractRadFIRFilter
```

ゼロ面積カスプ（ZAC）フィルタ。

フィルタの定義とフィルタ特性に関する議論については、["Improvement of the energy resolution via an optimized digital signal processing in GERDA Phase I", Eur. Phys. J. C 75, 255 (2015)](https://doi.org/10.1140/epjc/s10052-015-3409-6)を参照してください。

コンストラクタ:

  * `ZACChargeFilter(; fields...)`

フィールド:

  * `sigma::Union{Real, Unitful.AbstractQuantity{<:Real}}`: シェーピング時間 (τₛ) の同等物 デフォルト: 450
  * `toplen::Union{Real, Unitful.AbstractQuantity{<:Real}}`: フラットトップ (FT) の長さ デフォルト: 10
  * `tau::Union{Real, Unitful.AbstractQuantity{<:Real}}`: 指数の減衰定数 デフォルト: 20
  * `length::Union{Real, Unitful.AbstractQuantity{<:Real}}`: フィルタの総長 (L) デフォルト: 100
  * `beta::AbstractFloat`: スケーリングファクタ デフォルト: 100.0
