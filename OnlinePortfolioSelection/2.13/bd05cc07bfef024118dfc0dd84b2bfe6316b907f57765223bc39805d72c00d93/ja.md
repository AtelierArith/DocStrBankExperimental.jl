```
ppt(
  prices::AbstractMatrix,
  w::Int,
  ϵ::Int,
  horizon::Int,
  b̂ₜ::AbstractVector=ones(size(prices, 1))/size(prices, 1)
)
```

価格ピーク追跡（PPT）アルゴリズムを実行します。

# 引数

  * `prices::AbstractMatrix`: 価格の行列。
  * `w::Int`: ウィンドウサイズ。
  * `ϵ::Int`: 制約パラメータ。
  * `horizon::Int`: アルゴリズムを実行する日数。
  * `b̂ₜ::AbstractVector=ones(size(prices, 1))/size(prices, 1)`: 初期重み。

!!! warning "注意!"
    `prices` はサイズ `n_assets` × `n_periods` の行列である必要があります。


# 出力

  * `::OPSAlgorithm`: [`OPSAlgorithm`](@ref) 型のオブジェクト。

# 例

```julia
julia> using OnlinePortfolioSelection, YFinance

julia> tickers = ["AAPL", "AMZN", "GOOG", "MSFT"];

julia> querry = [get_prices(ticker, startdt="2019-01-01", enddt="2020-01-01")["adjclose"] for ticker in tickers];

julia> prices = stack(querry) |> permutedims;

julia> model = ppt(prices, 10, 100, 100);

julia> sum(model, dims=1) .|> isapprox(1.) |> all
true
```

# 参考文献

> [A Peak Price Tracking-Based Learning System for Portfolio Selection](https://doi.org/10.1109/TNNLS.2017.2705658)

