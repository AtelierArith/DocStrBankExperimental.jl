```
cellid(sim, name::Symbol, pos)
```

指定された位置 `pos` におけるラスタ `name` からエージェント（ノード）のIDを返します。`pos` は CartesianIndex または Dims{N} 型でなければなりません。

関連項目としては [`add_raster!`](@ref)、[`move_to!`](@ref)、[`add_edge!`](@ref) および [`agentstate`](@ref) があります。
