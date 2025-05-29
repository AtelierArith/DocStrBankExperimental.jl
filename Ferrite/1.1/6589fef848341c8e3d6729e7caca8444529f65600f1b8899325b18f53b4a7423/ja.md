```
getcells(grid::AbstractGrid)
getcells(grid::AbstractGrid, v::Union{Int,Vector{Int}})
getcells(grid::AbstractGrid, setname::String)
```

`<:AbstractGrid` のすべての `cells::Collection{C<:AbstractCell}` を返すか、`Int`、`Vector{Int}`、または `String` に基づいてサブセットを返します。最後のオプションは、`grid` の `cellset` を呼び出そうとします。`Collection` はインデックス可能な任意の型であり、`Grid` の場合は `Vector{C<:AbstractCell}` です。
