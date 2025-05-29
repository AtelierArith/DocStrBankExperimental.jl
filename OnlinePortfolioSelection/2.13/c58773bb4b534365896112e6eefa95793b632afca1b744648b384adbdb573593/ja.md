```
bs(adj_close::Matrix{T}; last_n::Int=0) where {T<:AbstractFloat}
```

与えられたデータに対してBest So Farアルゴリズムを実行します。

# 引数

  * `adj_close::Matrix{T}`: 資産の調整後終値の行列。

## キーワード引数

  * `last_n::Int`: 各資産のパフォーマンスを振り返る期間の数。`last_n`が0の場合、パフォーマンスは最初の期間から前の期間まで計算されます。

!!! warning "注意!"
    `adj_close`行列は資産 x 期間の順序である必要があります。


# 戻り値

  * `::OPSAlgorithm(n_assets, b, alg)`: `OPSAlgorithm`のインスタンス。

# 例

```julia
julia> using OnlinePortfolioSelection

julia> adj_close = rand(5, 10);

julia> model = bs(adj_close, last_n=2);

julia> model.b
5×10 Matrix{Float64}:
 0.2  0.0  0.0  0.0  1.0  0.0  0.0  0.0  0.0  0.0
 0.2  0.0  0.0  1.0  0.0  1.0  0.0  0.0  0.0  0.0
 0.2  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0  0.0
 0.2  1.0  1.0  0.0  0.0  0.0  1.0  0.0  1.0  1.0
 0.2  0.0  0.0  0.0  0.0  0.0  0.0  1.0  0.0  0.0

julia> sum(model.b, dims=1) .|> isapprox(1.) |> all
true
```

# 参考文献

> [KERNEL-BASED SEMI-LOG-OPTIMAL EMPIRICAL PORTFOLIO SELECTION STRATEGIES](https://doi.org/10.1142/S0219024907004251)

