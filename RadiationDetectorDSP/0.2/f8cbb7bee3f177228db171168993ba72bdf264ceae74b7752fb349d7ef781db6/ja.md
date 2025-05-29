```
struct Gauss1DFilter <: AbstractRadFIRFilter
```

1次元ガウスフィルターは次のように定義されます: f(x) = beta * exp(-0.5*(x/sigma)^2) / length

ここで、xは区間[-alpha*sigma, alpha*sigma]にあります。

コンストラクタ:

  * `Gauss1DFilter(; fields...)`

フィールド:

  * `sigma::Union{Real, Unitful.AbstractQuantity{<:Real}}`: 標準偏差 デフォルト: 1.0
  * `length::Union{Real, Unitful.AbstractQuantity{<:Real}}`: フィルターの全長 デフォルト: 100.0
  * `alpha::AbstractFloat`: ガウスウィンドウでカバーする標準偏差の量 デフォルト: 3.0
  * `beta::AbstractFloat`: スケーリングファクター デフォルト: 1.0
