```
ons(rel_pr::AbstractMatrix, β::Integer=1, 𝛿::AbstractFloat=1/8, η::AbstractFloat=0.)
```

オンラインニュートンステップ（ONS）アルゴリズムを実行します。

# 引数

  * `rel_pr::AbstractMatrix`: 相対価格。
  * `β::Integer=1`: ハイパーパラメータ。
  * `𝛿::AbstractFloat=1/8`: ヒューリスティック調整パラメータ。
  * `η::AbstractFloat=0.`: 学習率。

# 戻り値

  * `::OPSAlgorithm`: [`OPSAlgorithm`](@ref) オブジェクト。

# 例

```julia
julia> using OnlinePortfolioSelection, YFinance

julia> tickers = ["AAPL", "MSFT", "GOOG"];

julia> querry = [get_prices(ticker, startdt="2020-01-01", enddt="2020-01-12")["adjclose"] for ticker in tickers];

julia> prices = stack(querry, dims=1);

julia> rel_pr = prices[:, 2:end]./prices[:, 1:end-1];

julia> model = ons(rel_pr, 1, 0.005, 0.1);

julia> model.b
3×6 Matrix{Float64}:
 0.333333  0.333327  0.333293  0.333295  0.333319  0.333375
 0.333333  0.333302  0.333221  0.333182  0.333205  0.333184
 0.333333  0.333371  0.333486  0.333524  0.333475  0.333441
```

# 参考文献

> [Algorithms for Portfolio Management based on the Newton Method](https://doi.org/10.1145/1143844.1143846)

