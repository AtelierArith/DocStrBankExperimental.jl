```
MultipleEdge{T, U} <: AbstractMultipleEdge{T, U}
```

複数のエッジを表す構造体。

## 例

```jltestdoc
julia> using Graphs, Multigraphs

julia> me = MultipleEdge(1, 2, 3)
Multiple edge 1 => 2 with multiplicity 3

julia> for e in me println(e) end
Edge 1 => 2
Edge 1 => 2
Edge 1 => 2

```
