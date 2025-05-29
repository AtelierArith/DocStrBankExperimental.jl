```
tco(
  x::AbstractMatrix,
  w::Integer,
  horizon::Integer,
  𝛾::AbstractFloat,
  η::Integer,
  variant::Type{<:TCOVariant},
  b̂ₜ::Union{Nothing, AbstractVector}=nothing
)
```

トランザクションコスト最適化（TCO）アルゴリズムを実行します。

# 引数

  * `x::AbstractMatrix`: 相対価格の行列。
  * `w::Integer`: ウィンドウサイズ。
  * `horizon::Integer`: 投資のホライズン。
  * `𝛾`: トランザクションコストの率。
  * `η::Integer`: スムージングパラメータ。
  * `variant::Type{<:TCOVariant}`: アルゴリズムのバリアント。`TCO1` と `TCO2` の両方が実装されています。

## オプション引数

  * `b̂ₜ::Union{Nothing, AbstractVector}=nothing`: 最初のリバランスされたポートフォリオ。`nothing` が渡された場合、均一なポートフォリオが使用されます。

!!! warning "注意!"
    `x` はサイズ `n_assets` × `n_periods` の行列である必要があります。


# 戻り値

  * `::OPSAlgorithm`: [`OPSAlgorithm`](@ref) 型のオブジェクト。

# 例

```julia
julia> using OnlinePortfolioSelection, YFinance

julia> tickers = ["MSFT", "TSLA", "GOOGL", "NVDA"];

julia> querry = [get_prices(ticker, startdt="2024-01-01", enddt="2024-03-01")["adjclose"] for ticker in tickers];

julia> pr = stack(querry, dims=1);

julia> r = pr[:, 2:end]./pr[:, 1:end-1];

# TCO1
julia> model = tco(r, 5, 5, 0.04, 10, TCO1, [0.05, 0.05, 0.7, 0.2]);

julia> model.b
4×5 Matrix{Float64}:
 0.05  0.05  0.052937  0.0540085  0.0537137
 0.05  0.05  0.073465  0.0783877  0.0781003
 0.7   0.7   0.669571  0.657286   0.66002
 0.2   0.2   0.204027  0.210318   0.208166

# TCO2
julia> model = tco(r, 5, 5, 0.04, 10, TCO2, [0.05, 0.05, 0.7, 0.2]);

julia> model.b
4×5 Matrix{Float64}:
 0.05  0.0809567  0.0850694  0.0871646  0.0865584
 0.05  0.0809567  0.0830907  0.0890398  0.0885799
 0.7   0.730957   0.756827   0.746137   0.748113
 0.2   0.10713    0.0750128  0.0776584  0.0767483
```

# 参考

> [オンラインポートフォリオ選択のためのトランザクションコスト最適化](https://www.tandfonline.com/doi/full/10.1080/14697688.2017.1357831)

