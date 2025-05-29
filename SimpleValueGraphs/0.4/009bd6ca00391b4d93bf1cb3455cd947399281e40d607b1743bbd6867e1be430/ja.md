```
adjacency_matrix(g::AbstractValGraph)
```

グラフ `g` から `AdjacencyMatrix` ビューを作成します。

### 参照

[`AdjacencyMatrix`](@ref), [`ValMatrix`](@ref), [`weights`](@ref)

### 例

```jldoctest
julia> gv = ValGraph(star_graph(4), edgeval_types=(Float64,), edgeval_init=(s, d) -> (1.0, ))
{4, 3} undirected ValGraph with
              eltype: Int64
  vertex value types: ()
    edge value types: (Float64,)
   graph value types: ()

julia> adjacency_matrix(gv)
4×4 AdjacencyMatrix{ValGraph{Int64, Tuple{}, Tuple{Float64}, Tuple{}, Tuple{}, Tuple{Vector{Vector{Float64}}}}}:
 0  1  1  1
 1  0  0  0
 1  0  0  0
 1  0  0  0
```
