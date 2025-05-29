```
function ktpt(
  prices::AbstractMatrix,
  horizon::S,
  w::S,
  q::S,
  η::S,
  ν::T,
  p̂ₜ::AbstractVector,
  b̂ₜ::Union{Nothing, AbstractVector{T}}
) where {S<:Integer, T<:AbstractFloat}
```

ポートフォリオ最適化モデルのためのカーネルベースのトレンドパターントラッキングシステムを実行します。

!!! note "重要な注意"
    この関数を使用するには、まず[Lasso.jl](https://github.com/JuliaStats/Lasso.jl)パッケージをインストールし、その後OnlinePortfolioSelection.jlパッケージと一緒にインポートする必要があります：

    ```julia
    julia> using Pkg; Pkg.add("Lasso")
    julia> using Lasso, OnlinePortfolioSelection
    ```


# 引数

  * `prices::AbstractMatrix`: 資産の日次価格の行列。
  * `horizon::S`: アルゴリズムを実行するためのホライズン。
  * `w::S`: ウィンドウサイズ。
  * `q::S`: 係数。
  * `η::S`: ポートフォリオを最適化するためのステップサイズ。
  * `ν::T`: ℓ1およびℓ2正則化の割合を調整するミキシングパラメータ。
  * `p̂ₜ::AbstractVector`: 時間`t`におけるサイズ`n_assets`のベクトル。
  * `b̂ₜ::Union{Nothing, AbstractVector{T}}`: 時間`t`におけるポートフォリオの重みのベクトル。

!!! warning "注意!"
    `prices`はサイズ`n_assets` × `n_periods`の行列である必要があります。


# 戻り値

  * `::OPSAlgorithm`: [`OPSAlgorithm`](@ref)オブジェクト。

# 例

```julia
julia> using OnlinePortfolioSelection, YFinance, Lasso

julia> tickers = ["GOOG", "AAPL", "MSFT", "AMZN"];

julia> querry = [get_prices(ticker, startdt="2020-01-01", enddt="2020-01-31")["adjclose"] for ticker=tickers];

julia> prices = stack(querry, dims=1);

julia> h, w, q, eta, v, phat_t, bhat_t = 5, 5, 6, 1000, 0.5, rand(length(tickers)), nothing

julia> model = ktpt(prices, h, w, q, eta, v, phat_t, bhat_t);

julia> model.b
4×5 Matrix{Float64}:
 0.25  0.0  1.0  1.0  1.0
 0.25  0.0  0.0  0.0  0.0
 0.25  1.0  0.0  0.0  0.0
 0.25  0.0  0.0  0.0  0.0
```

# 参考

> [ポートフォリオ最適化のためのカーネルベースのトレンドパターントラッキングシステム](https://doi.org/10.1007/s10618-018-0579-5)

