```
AdjacencyMatrix(g::AbstractGraph)
```

グラフの行列ビュー。

エントリ `(i, j)` は、`i -> j` が `g` のエッジであれば `true`、そうでなければ `false` です。

これはビューとして、基になるグラフが変更されると、この行列のエントリとサイズが変わる可能性があります。ビュー自体は不変です。グラフが変更されても変わらない可変行列を得るには、`Matrix` または `SparseMatrixCSC` に変換してください。

### 参照

[`adjacency_matrix`](@ref), [`ValMatrix`](@ref), [`weigths`](@ref)

### 例

```jldoctest
julia> g = complete_bipartite_graph(2, 2)
{4, 4} undirected simple Int64 graph

julia> AdjacencyMatrix(g)
4×4 AdjacencyMatrix{SimpleGraph{Int64}}:
 0  0  1  1
 0  0  1  1
 1  1  0  0
 1  1  0  0

julia> AdjacencyMatrix(g) |> Matrix
4×4 Matrix{Bool}:
 0  0  1  1
 0  0  1  1
 1  1  0  0
 1  1  0  0
```
