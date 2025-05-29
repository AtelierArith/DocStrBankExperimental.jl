```
anticor(adj_close::Matrix{T}, window::Int) where {T<:Real}
```

`adj_close`に対してウィンドウサイズ`window`でAnticorアルゴリズムを実行します。

!!! warning "注意!"
    `adj_close`はサイズ`n_assets` × `n_periods`の行列である必要があります。


# 引数

  * `adj_close::Matrix{T}`: 調整後終値の行列
  * `window::Int`: ウィンドウのサイズ

# 戻り値

  * `::OPSAlgorithm(n_assets, b, alg)`: OPSAlgorithmオブジェクト。

# 例

```julia
julia> using OnlinePortfolioSelection

julia> adj_close = [
       1. 2.
       4. 9.
       7. 8.
       10. 11.
       13. 7.
       8. 17.
       19. 20.
       22. 23.
       25. 8.
       2. 12.
       5. 12.
       5. 0.
       0. 2.
       1. 1.
       ];

julia> adj_close = permutedims(adj_close);

julia> m_anticor = anticor(adj_close, 3);

julia> m_anticor.b
2×14 Matrix{Float64}:
 0.5  0.5  0.5  0.5  …  0.0  0.0  0.0  1.0
 0.5  0.5  0.5  0.5     1.0  1.0  1.0  0.0

julia> sum(m_anticor.b, dims=1) .|> isapprox(1., atol=1e-8) |> all
true
```

# 参考文献

> [Can We Learn to Beat the Best Stock](https://www.doi.org/10.1613/jair.1336)

