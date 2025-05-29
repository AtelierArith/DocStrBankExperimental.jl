```
uniform(n_assets::Int, horizon::Int)
```

均等ポートフォリオを構築します。

# 引数

  * `n_assets::Int`: 資産の数。
  * `horizon::Int`: 投資期間の数。

# 戻り値

  * `::OPSAlgorithm`: [`OPSAlgorithm`](@ref) 型のオブジェクト。

# 例

```julia
julia> using OnlinePortfolioSelection

julia> model = uniform(3, 10)

julia> sum(model.b, dims=1) .|> isapprox(1.) |> all
true
```
