```
load(adj_close::AbstractMatrix{T}, α::T, ω::S, horizon::S, η::T, ϵ::T=1.5) where {T<:AbstractFloat, S<:Int}
```

LOADアルゴリズムを実行します。

# 引数

  * `adj_close::AbstractMatrix{T}`: 調整後終値データ。
  * `α::T`: 減衰係数。 (0 < α < 1)
  * `ω::S`: ウィンドウサイズ。 (ω > 0)
  * `horizon::S`: 投資の時間枠。 (n_periods > horizon > 0)
  * `η::T`: 閾値。 (η > 0)
  * `ϵ::T=1.5`: 期待リターンの閾値。

!!! warning "注意!"
    `adj_close`はサイズが `n_assets` × `n_periods` の行列である必要があります。


# 戻り値

  * `::OPSAlgorithm`: 各期間の各資産の重みを含む `OPSAlgorithm` 型のオブジェクト。

# 例

```julia
# データを取得
julia> using YFinance
julia> startdt, enddt = "2022-04-01", "2023-04-27";
julia> querry = [
          get_prices(ticker, startdt=startdt, enddt=enddt)["adjclose"] for ticker in tickers
       ];
julia> prices = reduce(hcat, querry);
julia> prices = permutedims(prices);

julia> using OnlinePortfolioSelection

julia> model = load(prices, 0.5, 30, 5, 0.1);

julia> model.b
5×5 Matrix{Float64}:
 0.2  2.85298e-8  0.0        0.0       0.0
 0.2  0.455053    0.637299   0.694061  0.653211
 0.2  0.215388    0.0581291  0.0       0.0
 0.2  0.329559    0.304572   0.305939  0.346789
 0.2  6.06128e-9  0.0        0.0       0.0

julia> sum(model.b, dims=1) .|> isapprox(1.) |> all
true
```

# 参考文献

> [オンラインポートフォリオ選択のためのローカル適応学習システム](https://doi.org/10.1016/j.knosys.2019.104958)

