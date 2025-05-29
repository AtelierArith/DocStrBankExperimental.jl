```
rmr(p::AbstractMatrix, horizon::Integer, w::Integer, ϵ, m, τ)
```

ロバストメディアンリバージョン（RMR）アルゴリズムを実行します。

# 引数

  * `p::AbstractMatrix`: 価格行列。
  * `horizon::Integer`: アルゴリズムを実行する期間の数。
  * `w::Integer`: ウィンドウサイズ。
  * `ϵ`: リバージョン閾値。
  * `m`: 最大反復回数。
  * `τ`: 許容レベル。

# 戻り値

  * `OPSAlgorithm`: [`OPSAlgorithm`](@ref) オブジェクト。

# 例

```julia
julia> using OnlinePortfolioSelection, YFinance

julia> tickers = ["GOOG", "AAPL", "MSFT", "AMZN"];

julia> querry = [get_prices(ticker, startdt="2020-01-01", enddt="2020-01-31")["adjclose"] for ticker=tickers];

julia> prices = stack(querry, dims=1);

julia> horizon = 5

julia> window = 5

julia> ϵ = 5

julia> m = 7

julia> τ = 1e6

julia> model = rmr(prices, horizon, window, ϵ, m, τ);

julia> model.b
4×5 Matrix{Float64}:
 0.25  1.0         1.0       1.0         1.0
 0.25  0.0         0.0       0.0         0.0
 0.25  0.0         0.0       0.0         0.0
 0.25  1.14513e-8  9.979e-9  9.99353e-9  1.03254e-8
```

# 参考

> [オンラインポートフォリオ選択のためのロバストメディアンリバージョン戦略](https://www.doi.org/10.1109/TKDE.2016.2563433)

