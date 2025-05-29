```
sspo(
  p::AbstractMatrix,
  horizon::Integer,
  w::Integer,
  b̂ₜ::Union{Nothing, AbstractVector}=nothing,
  η::AbstractFloat=0.005,
  γ::AbstractFloat=0.01,
  λ::AbstractFloat=0.5,
  ζ::Integer=500,
  ϵ::AbstractFloat=1e-4,
  max_iter=1e4
)
```

短期スパースポートフォリオ最適化（SSPO）アルゴリズムを実行します。

# 引数

  * `p::AbstractMatrix`: 資産の価格。
  * `horizon::Integer`: 投資期間の数。
  * `w::Integer`: ウィンドウサイズ。
  * `b̂ₜ::Union{Nothing, AbstractVector}=nothing`: 初期ポートフォリオの重み。`nothing`が渡された場合、最初の期間には均等ポートフォリオが選択されます。
  * `η::AbstractFloat=0.005`: 学習率。
  * `γ::AbstractFloat=0.01`: 正則化パラメータ。
  * `λ::AbstractFloat=0.5`: 正則化パラメータ。
  * `ζ::Integer=500`: 正則化パラメータ。
  * `ϵ::AbstractFloat=1e-4`: アルゴリズムの収束に対する許容誤差。
  * `max_iter=1e4`: 最大反復回数。

# 戻り値

  * `::OPSAlgorithm`: [`OPSAlgorithm`](@ref)オブジェクト。

# 例

```julia
julia> using OnlinePortfolioSelection, YFinance

julia> tickers = ["GOOG", "AAPL", "MSFT", "AMZN"]

julia> querry = [get_prices(ticker, startdt="2020-01-01", enddt="2020-01-31")["adjclose"] for ticker=tickers]

julia> prices = stack(querry, dims=1)

julia> h = 5

julia> w = 5

julia> model = sspo(prices, h, w);

julia> model.b
4×5 Matrix{Float64}:
 0.25  9.92018e-9  1.0         1.0  1.0
 0.25  0.0         0.0         0.0  0.0
 0.25  0.0         0.0         0.0  0.0
 0.25  1.0         9.94367e-9  0.0  0.0
```

# 参考

> [短期スパースポートフォリオ最適化に関する交互方向法に基づく](http://jmlr.org/papers/v19/17-558.html)

