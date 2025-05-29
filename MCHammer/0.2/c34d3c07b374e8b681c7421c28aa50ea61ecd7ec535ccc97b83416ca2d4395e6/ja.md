```
forecast_uncertainty(HistoricalData::Vector{<:Real}, PeriodsToForecast::Int) -> Vector{Float64}
```

歴史的データのボラティリティに基づいて予測不確実性の乗数を計算します。

この関数は、歴史的データからのパーセンテージリターンを計算し、それらのリターンの標準偏差（σ）を推定し、予測乗数のベクトルを生成します。各乗数は次のように計算されます：

$$
u = 1 + \sigma \cdot \epsilon
$$

ここで、($\epsilon$) は標準正規分布から抽出されたランダムサンプル          $\epsilon \sim \mathcal{N}(0,1)$ であり、$\sigma$ は歴史的パーセンテージリターンの標準偏差です。

# 引数

  * `HistoricalData::Vector{<:Real}`: 歴史的観測値のベクトル（例：価格、値）。
  * `PeriodsToForecast::Int`: 不確実性の乗数を生成するための予測期間の数。

# 戻り値

  * 予測不確実性の乗数を含む長さ `PeriodsToForecast` のベクトル。これらの乗数は、基本予測を摂動させて予測の変動性をシミュレートするために使用できます。
