```
cornu(
  x::AbstractMatrix{T},
  horizon::M,
  w::M;
  rho::T=0.2,
  init_budg=1,
  progress::Bool=false
) where {T<:AbstractFloat, M<:Integer}
```

CORN-Uアルゴリズムを実行します。

# 引数

  * `x::AbstractMatrix{T}`: 資産の価格相対行列。
  * `horizon::M`: 投資する期間の数。
  * `w::M`: 検討する最大時間ウィンドウの長さ。

## キーワード引数

  * `rho::T=0.2`: 相関係数の閾値。
  * `init_budg=1`: 投資のための初期予算。
  * `progress::Bool=false`: 進捗バーを表示するかどうか。

!!! warning "注意!"
    `x`はサイズ`n_assets` × `n_periods`の行列である必要があります。


# 戻り値

  * `::OPSAlgorithm`: [`OPSAlgorithm`](@ref)型のオブジェクト。

# 例

```julia
julia> using OnlinePortfolioSelection

julia> x = rand(5, 100);

julia> model = cornu(x, 10, 5, 0.5);

julia> model.alg
"CORN-U"

julia> sum(model.b, dims=1) .|> isapprox(1.) |> all
true
```

[`cornk`](@ref)および[`dricornk`](@ref)を参照してください。

# 参考文献

> [CORN: Correlation-driven nonparametric learning approach for portfolio selection](https://doi.org/10.1145/1961189.1961193)

