```
bcrp(rel_pr::AbstractMatrix{T}) where T<:AbstractFloat
```

Run Best Constant Rebalanced Portfolio (BCRP) algorithm.

# 引数

  * `rel_pr::AbstractMatrix{T}`: 相対価格行列。

!!! warning "注意!"
    `rel_pr` はサイズ `n_assets` × `n_periods` の行列である必要があります。


# 戻り値

  * `::OPSAlgorithm`: [`OPSAlgorithm`](@ref) オブジェクト

# 例

```julia
julia> using OnlinePortfolioSelection

julia> rel_pr = rand(3, 8);

julia> m_bcrp = bcrp(rel_pr);

julia> m_bcrp.b
3×8 Matrix{Float64}:
 8.58038e-9  8.58038e-9  8.58038e-9  8.58038e-9  8.58038e-9  8.58038e-9  8.58038e-9  8.58038e-9
 1.0         1.0         1.0         1.0         1.0         1.0         1.0         1.0
 0.0         0.0         0.0         0.0         0.0         0.0         0.0         0.0

julia> sum(m_bcrp.b, dims=1) .|> isapprox(1.) |> all
true
```

# 参考文献

> [Universal Portfolios](https://onlinelibrary.wiley.com/doi/10.1111/j.1467-9965.1991.tb00002.x)

