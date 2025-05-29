```
point_sets(body)
```

`body`のすべてのポイントセットを返します。

# 引数

  * `body::AbstractBody`: [`Body`](@ref)。

# 例

```julia-repl
julia> body = Body(BBMaterial(), rand(3,100), rand(100))
100-point Body{BBMaterial{NoCorrection}}:
  100-point set `all_points`

julia> point_set!(body, :set_a, 1:10) # 最初の10ポイント

julia> Peridynamics.point_sets(body)
Dict{Symbol, Vector{Int64}} with 2 entries:
  :all_points => [1, 2, 3, 4, 5, 6, 7, 8, 9, 10  …  91, 92, 93, 94, 95, 96, 97, 98, 9…
  :set_a      => [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```
