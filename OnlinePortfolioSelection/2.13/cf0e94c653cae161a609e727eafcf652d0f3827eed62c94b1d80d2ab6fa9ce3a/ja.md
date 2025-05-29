```
mrvol(
  rel_pr::AbstractMatrix{T},
  rel_vol::AbstractMatrix{T},
  horizon::S,
  Wₘᵢₙ::S,
  Wₘₐₓ::S,
  λ::T,
  η::T
) where {T<:AbstractFloat, S<:Integer}
```

MRvolアルゴリズムを実行します。

# 引数

  * `rel_pr::AbstractMatrix{T}`: 各資産の各日の終値と始値の比率を表す相対価格行列。
  * `rel_vol::AbstractMatrix{T}`: 𝘷ᵢⱼが資産𝑖のtᵗʰ取引量を(t - 1)ᵗʰ取引量で割った相対ボリューム行列。
  * `horizon::S`: 投資の時間枠。アルゴリズムを実行するためにデータの最後の`horizon`日が使用されます。
  * `Wₘᵢₙ::S`: 最小ウィンドウサイズ。
  * `Wₘₐₓ::S`: 最大ウィンドウサイズ。
  * `λ::T`: 損失関数におけるトレードオフパラメータ。
  * `η::T`: 学習率。

!!! warning "注意!"
    `rel_pr`と`rel_vol`はサイズ`n_assets` × `n_periods`の行列である必要があります。


# 戻り値

  * `::OPSAlgorithm`: [`OPSAlgorithm`](@ref)オブジェクト。

# 例

```julia
julia> using OnlinePortfolioSelection, YFinance

julia> tickers = ["AAPL", "MSFT", "GOOG"];

julia> startdt, enddt = "2019-01-01", "2020-01-01";

julia> querry_open_price = [get_prices(ticker, startdt=startdt, enddt=enddt)["open"] for ticker in tickers];

julia> open_pr = reduce(hcat, querry_open_price) |> permutedims;

julia> querry_close_pr = [get_prices(ticker, startdt=startdt, enddt=enddt)["adjclose"] for ticker in tickers];

julia> close_pr = reduce(hcat, querry_close_pr) |> permutedims;

julia> querry_vol = [get_prices(ticker, startdt=startdt, enddt=enddt)["vol"] for ticker in tickers];

julia> vol = reduce(hcat, querry_vol) |> permutedims;

julia> rel_pr = (close_pr ./ open_pr)[:, 2:end];

julia> rel_vol = vol[:, 2:end] ./ vol[:, 1:end-1];

julia> size(rel_pr) == size(rel_vol)
true

julia> horizon = 100; Wₘᵢₙ = 4; Wₘₐₓ = 10; λ = 0.05; η = 0.01;

julia> r = mrvol(rel_pr, rel_vol, horizon, Wₘᵢₙ, Wₘₐₓ, λ, η);

julia> r.b
3×100 Matrix{Float64}:
 0.333333  0.0204062  0.0444759  …  0.38213   0.467793
 0.333333  0.359864   0.194139      0.213264  0.281519
 0.333333  0.61973    0.761385      0.404606  0.250689
```

# 参考文献

> [専門家戦略の統合に基づくオンラインポートフォリオ選択：平均回帰と取引量。](https://doi.org/10.1016/j.eswa.2023.121472)

