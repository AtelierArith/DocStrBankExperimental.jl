```
cornk(
  x::AbstractMatrix{<:AbstractFloat},
  horizon::T,
  k::T,
  w::T,
  p::T;
  init_budg=1,
  progress::Bool=false
) where T<:Integer
```

CORN-Kアルゴリズムを実行します。

# 引数

  * `x::AbstractMatrix{<:AbstractFloat}`: 資産の価格相対行列。
  * `horizon::T`: 投資する期間の数。
  * `k::T`: 選択するトップ専門家の数。
  * `w::T`: 検討する最大時間ウィンドウの長さ。
  * `p::T`: 相関係数の閾値の最大数。

## キーワード引数

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

julia> model = cornk(x, 10, 3, 5, 3);

julia> model.alg
"CORN-K"

julia> sum(model.b, dims=1) .|> isapprox(1.) |> all
true
```

[`cornu`](@ref)および[`dricornk`](@ref)を参照してください。

# 参考文献

> [CORN: Correlation-driven nonparametric learning approach for portfolio selection](https://doi.org/10.1145/1961189.1961193)

