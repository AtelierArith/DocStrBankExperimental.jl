```
caeg(rel_pr::AbstractMatrix, ηs::AbstractVector)
```

CAEGアルゴリズムを実行します。

# 引数

  * `rel_pr::AbstractMatrix`: 歴史的相対価格。論文の著者は*「終値と前回の終値の比率」*を使用しました。
  * `ηs::AbstractVector`: 学習率。

!!! warning "注意!"
    `rel_pr`はサイズ`n_assets` × `n_periods`の行列である必要があります。


# 戻り値

  * `::OPSAlgorithm`: [`OPSAlgorithm`](@ref)オブジェクト。

# 例

```julia
julia> using OnlinePortfolioSelection, YFinance

julia> tickers = ["AAPL", "MSFT", "GOOG"];

julia> startdt, enddt = "2020-1-1", "2020-1-10";

julia> open_querry = [get_prices(ticker, startdt=startdt, enddt=enddt)["open"] for ticker ∈ tickers];

julia> open_ = stack(open_querry) |> permutedims;

julia> close_querry = [get_prices(ticker, startdt=startdt, enddt=enddt)["adjclose"] for ticker ∈ tickers];

julia> close_ = stack(close_querry) |> permutedims;

julia> rel_pr = close_./open_;

julia> learning_rates = [0.02, 0.05];

julia> model = caeg(rel_pr, learning_rates);

julia> model.b
3×6 Matrix{Float64}:
 0.333333  0.333322  0.333286  0.333271  0.333287  0.333368
 0.333333  0.333295  0.333271  0.333171  0.333123  0.333076
 0.333333  0.333383  0.333443  0.333558  0.33359   0.333557
```

# 参考文献

> [オンラインポートフォリオ選択のための指数的勾配専門家の助言の集約](https://doi.org/10.1080/01605682.2020.1848358)

