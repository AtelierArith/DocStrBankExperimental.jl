```
function rprt(
  rel_pr::AbstractMatrix{T},
  horizon::Integer,
  w::Integer=5,
  ϑ::T=0.8,
  𝜖::Integer=50,
  bₜ::Union{Nothing, AbstractVector}=nothing
) where T<:AbstractFloat
```

RPRTアルゴリズムを実行します。

# 引数

  * `rel_pr::AbstractMatrix{T}`: 相対価格の `資産 × サンプル` 行列。
  * `horizon::Integer`: 投資期間。
  * `w::Integer=5`: ウィンドウの長さ。
  * `ϑ::T=0.8`: 混合パラメータ。
  * `𝜖::Integer=50`: 期待される利益レベル。
  * `bₜ::Union{Nothing, AbstractVector}=nothing`: 初期ポートフォリオ。デフォルト値は均一なポートフォリオになります。

!!! warning "注意!"
    `rel_pr` はサイズ `n_assets` × `n_periods` の行列である必要があります。


# 戻り値

  * `::OPSAlgorithm`: [`OPSAlgorithm`](@ref) 型のオブジェクト。

# 例

```julia
julia> using OnlinePortfolioSelection

julia> rel_pr = rand(3, 6);
julia> horizon = 2
julia> window = 3
julia> v = 0.2
julia> eps = 10
julia> b = [0.5, 0.3, 0.2];

julia> m_rprt = rprt(rel_pr, horizon, window, v, eps, b);

julia> m_rprt.b
3×2 Matrix{Float64}:
 0.5  1.0
 0.3  0.0
 0.2  2.03615e-10

julia> sum(m_rprt.b, dims=1) .|> isapprox(1.) |> all
true
```

# 参考

> [自動ポートフォリオ最適化のための再加重価格相対追跡システム](https://ieeexplore.ieee.org/document/8411138/)

