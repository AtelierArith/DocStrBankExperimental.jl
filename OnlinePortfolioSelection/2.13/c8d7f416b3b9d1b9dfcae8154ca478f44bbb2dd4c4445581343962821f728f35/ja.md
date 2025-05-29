```
aictr(
  prices::AbstractMatrix,
  horizon::Integer,
  w::Integer,
  ϵ::Integer,
  σ::AbstractVector,
  trend_model::AbstractVector{<:TrendRep};
  bt::AbstractVector = ones(size(prices, 1))/size(prices, 1)
)
```

適応入力および複合トレンド表現（AICTR）アルゴリズムを実行します。

# 引数

  * `prices::AbstractMatrix`: 価格の行列。
  * `horizon::Integer`: 投資日数。
  * `w::Integer`: ウィンドウサイズ。
  * `ϵ::Integer`: 更新強度。
  * `σ::AbstractVector`: 各トレンド表現の標準偏差を含むサイズ `L` のベクトル。
  * `trend_model::AbstractVector{<:TrendRep}`: トレンド表現のベクトル。 [`SMAP`](@ref)、[`EMA`](@ref)、および[`PP`](@ref)がサポートされています。

## キーワード引数

  * `bt::AbstractVector`: サイズ `n_assets` の初期ポートフォリオベクトル。

!!! 警告 "注意"     `prices` はサイズ `n_assets` × `n_periods` の行列である必要があります。

# 戻り値

  * `::OPSAlgorithm`: [`OPSAlgorithm`](@ref) 型のオブジェクト。

# 例

```julia
julia> using OnlinePortfolioSelection, YFinance

julia> tickers = ["AAPL", "MSFT", "GOOG", "AMZN", "META", "TSLA", "BRK-A", "NVDA", "JPM", "JNJ"];

julia> querry = [get_prices(ticker, startdt="2019-01-01", enddt="2019-12-31")["adjclose"] for ticker ∈ tickers];

julia> prices = stack(querry) |> permutedims;

julia> horizon = 5;

julia> w = 3;

julia> ϵ = 500;

julia> σ = [0.5, 0.5];

julia> models = [SMAP(), EMA(0.5)];

julia> bt = [0.3, 0.3, 0.4];

julia> model = aictr(prices, horizon, w, ϵ, σ, models)

julia> model.b
10×5 Matrix{Float64}:
 0.1  0.0         0.0         0.0         0.0
 0.1  0.0         0.0         0.0         0.0
 0.1  1.0         6.92439e-8  0.0         0.0
 0.1  0.0         0.0         0.0         0.0
 0.1  0.0         1.0         0.0         0.0
 0.1  0.0         0.0         0.0         0.0
 0.1  6.92278e-8  0.0         0.0         0.0
 0.1  0.0         0.0         6.95036e-8  1.0
 0.1  0.0         0.0         0.0         0.0
 0.1  0.0         0.0         1.0         6.95537e-8
```

# 参考文献

> [適応入力および複合トレンド表現を用いたポートフォリオ選択のための放射基底関数](https://www.doi.org/10.1109/TNNLS.2018.2827952)

