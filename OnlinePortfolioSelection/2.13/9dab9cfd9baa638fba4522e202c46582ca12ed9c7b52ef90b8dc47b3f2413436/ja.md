```
tppt(
  prices::AbstractMatrix,
  horizon::Integer,
  w::Integer,
  ϵ::Integer=100,
  α::AbstractFloat=0.5
)
```

トレンドプロモート価格追跡（TPPT）アルゴリズムを実行します。

# 引数

  * `prices::AbstractMatrix`: 資産の価格。各列は期間を表し、各行は資産を表します。
  * `horizon::Integer`: 投資期間の数。
  * `w::Integer`: ウィンドウサイズ。
  * `ϵ::Integer`: 制約パラメータ。
  * `α::AbstractFloat`: 指数移動平均パラメータ。

# 戻り値

  * `::OPSAlgorithm`: [`OPSAlgorithm`](@ref) オブジェクト。

# 例

```julia
julia> using OnlinePortfolioSelection, YFinance

julia> tickers = ["AAPL", "MSFT", "GOOG"];

julia> querry = [get_prices(ticker, startdt="2020-01-01", enddt="2020-01-12")["adjclose"] for ticker in tickers];

julia> prices = stack(querry, dims=1);

julia> horizon, w = 3, 3;

julia> model = tppt(prices, horizon, w);

julia> model.b
3×3 Matrix{Float64}:
 0.333333  1.52594e-6  7.35766e-7
 0.333333  5.30452e-6  3.90444e-6
 0.333333  0.999993    0.999995
```

# 参考文献

> [トレンドプロモート価格追跡アンサンブル学習アルゴリズムに基づくオンラインポートフォリオ戦略](https://doi.org/10.1016/j.knosys.2021.107957)

