```
bk(rel_price::AbstractMatrix{T}, K::S, L::S, c::T) where {T<:AbstractFloat, S<:Integer}
```

Bᴷアルゴリズムを実行します。

# 引数

  * `rel_price::AbstractMatrix{T}`: 資産の相対価格。
  * `K::S`: エキスパートの数。
  * `L::S`: 時間ウィンドウの数。
  * `c::T`: 類似性の閾値。

!!! warning "注意!"
    `rel_price` はサイズ `n_assets` × `n_periods` の行列である必要があります。


# 戻り値

  * `::OPSAlgorithm`: [`OPSAlgorithm`](@ref) 型のオブジェクト。

# 例

```julia
julia> using OnlinePortfolioSelection

julia> daily_relative_prices = rand(3, 20);
julia> nexperts = 10;
julia> nwindows = 3;
julia> sim_thresh = 0.5;

julia> model = bk(daily_relative_prices, nexperts, nwindows, sim_thresh);

julia> model.b
3×20 Matrix{Float64}:
 0.333333  0.333333  0.354839  0.318677  …  0.333331  0.329797  0.322842  0.408401
 0.333333  0.333333  0.322581  0.362646     0.333339  0.340406  0.354317  0.295811
 0.333333  0.333333  0.322581  0.318677     0.333331  0.329797  0.322842  0.295789

julia> sum(model.b, dims=1) .|> isapprox(1.) |> all
true
```

# 参考

> [NONPARAMETRIC KERNEL-BASED SEQUENTIAL INVESTMENT STRATEGIES](https://doi.org/10.1111/j.1467-9965.2006.00274.x)

