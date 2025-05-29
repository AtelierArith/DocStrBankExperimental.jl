```
function up(
  rel_pr::AbstractMatrix{T};
  eval_points::Integer=10^4
) where T<:AbstractFloat
```

ユニバーサルポートフォリオ（UP）アルゴリズム。

与えられた過去の価格とパラメータを使用して、ユニバーサルポートフォリオ（UP）の重みと予算を計算します。

# 引数

  * `rel_pr::AbstractMatrix{T}`: 過去の相対価格。

## キーワード引数

  * `eval_points::Integer=10^4`: 評価ポイントの数。

!!! warning "注意!"
    `rel_pr` はサイズ `n_assets` × `n_periods` の行列である必要があります。


# 戻り値

  * `::OPSAlgorithm`: [`OPSAlgorithm`](@ref) オブジェクト。

# 例

```julia
julia> using OnlinePortfolioSelection

julia> rel_pr = rand(3, 9);

julia> m_up = up(rel_pr);

julia> m_up.b
3×9 Matrix{Float64}:
 0.333333  0.272709  0.345846  0.385378  0.308659  0.328867  0.280564  0.349619  0.433529
 0.333333  0.288016  0.315603  0.249962  0.252828  0.24165   0.270741  0.2621    0.235743
 0.333333  0.439276  0.338551  0.364661  0.438512  0.429483  0.448695  0.388281  0.330729

julia> sum(m_up.b, dims=1) .|> isapprox(1.) |> all
true
```

# 参考文献

> [ユニバーサルポートフォリオ](https://doi.org/10.1111/j.1467-9965.1991.tb00002.x)

