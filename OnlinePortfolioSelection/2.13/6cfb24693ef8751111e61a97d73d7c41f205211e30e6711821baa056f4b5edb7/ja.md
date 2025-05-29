```
dricornk(
  x::AbstractMatrix{T},
  relpr_market::AbstractVector{T},
  horizon::M,
  k::M,
  w::M,
  p::M;
  lambda::T=1e-3,
  init_budg=1,
  progress::Bool=false
) where {T<:AbstractFloat, M<:Integer}
```

DRICORNKアルゴリズムを実行します。

# 引数

  * `x::AbstractMatrix{T}`: 資産の相対価格の行列。
  * `relpr_market::AbstractVector{T}`: 同じ期間の市場の相対価格のベクトル。
  * `horizon::M`: 投資のホライズン。
  * `k::M`: 専門家の数。
  * `w::M`: 検討される最大の時間ウィンドウの長さ。
  * `p::M`: 相関係数の閾値の最大数。

## キーワード引数

  * `lambda::T=1e-3`: 正則化パラメータ。
  * `init_budg=1`: 投資の初期予算。
  * `progress::Bool=false`: 進捗バーを表示するかどうか。

!!! warning "注意!"
    `x`はサイズ`n_assets` × `n_periods`の行列である必要があります。


# 戻り値

  * `::OPSAlgorithm`: [`OPSAlgorithm`](@ref)型のオブジェクト。

# 例

```julia
julia> using OnlinePortfolioSelection

julia> stocks_ret, market_ret = rand(10, 100), rand(100);

julia> m_dricornk = dricornk(stocks_ret, market_ret, 5, 2, 4, 3);

julia> sum(m_dricornk.b, dims=1) .|> isapprox(1.) |> all
true
```

[`cornk`](@ref)および[`cornu`](@ref)を参照してください。

# 参考文献

> [DRICORN-K: A Dynamic RIsk CORrelation-driven Non-parametric Algorithm for Online Portfolio Selection](https://www.doi.org/10.1007/978-3-030-66151-9_12)

