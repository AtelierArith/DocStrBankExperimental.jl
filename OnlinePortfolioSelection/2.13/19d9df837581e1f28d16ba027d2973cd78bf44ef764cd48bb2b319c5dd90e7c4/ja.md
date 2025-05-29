```
spolc(x::AbstractMatrix, 𝛾::AbstractFloat, w::Integer)
```

短期ポートフォリオ最適化のためのランク1共分散推定を用いた損失制御戦略を実行します（SPOLC）。

# 引数

  * `x::AbstractMatrix`: 相対価格の行列。
  * `𝛾::AbstractFloat`: 増加因子とリスクのトレードオフを行う混合パラメータ。
  * `w::Integer`: ウィンドウサイズ。

!!! warning "注意!"
    `x` はサイズ `n_assets` × `n_periods` の行列である必要があります。


# 戻り値

  * `::OPSAlgorithm`: [`OPSAlgorithm`](@ref) のオブジェクト。

# 例

```julia
julia> using OnlinePortfolioSelection, YFinance

julia> tickers = ["AAPL", "AMZN", "GOOG", "MSFT"];

julia> querry = [get_prices(ticker, startdt="2019-01-01", enddt="2019-01-25")["adjclose"] for ticker in tickers];

julia> prices = stack(querry, dims=1);

julia> rel_pr = prices[:, 2:end] ./ prices[:, 1:end-1];

julia> model = spolc(rel_pr, 0.025, 5);

julia> model.b
4×15 Matrix{Float64}:
 0.25  0.197923  0.244427  0.239965  …  0.999975    8.49064e-6  2.41014e-6
 0.25  0.272289  0.251802  0.276544     1.57258e-5  0.999983    0.999992
 0.25  0.269046  0.255524  0.240024     6.50008e-6  5.94028e-6  3.69574e-6
 0.25  0.260742  0.248247  0.243466     2.99939e-6  3.04485e-6  1.56805e-6

julia> sum(model.b, dims=1) .|> isapprox(1.) |> all
true
```

# 参考

> [短期ポートフォリオ最適化のためのランク1共分散推定による損失制御](https://dl.acm.org/doi/abs/10.5555/3455716.3455813)

