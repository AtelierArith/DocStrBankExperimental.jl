```
add_vertex!(model::ABM{<:GraphSpace})
```

モデルのグラフに新しいノード（すなわち、可能な位置）を追加し、それを返します。この新しいノードは、既存のノードと[`add_edge!`](@ref)を使用して接続できます。
