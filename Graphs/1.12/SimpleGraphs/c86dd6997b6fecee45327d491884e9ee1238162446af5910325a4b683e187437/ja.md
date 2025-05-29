```
SimpleGraph{T}(adjm::AbstractMatrix)
```

隣接行列 `adjm` から `SimpleGraph{T}` を構築します。もし `adjm[i][j] != 0` であれば、辺 `(i, j)` が挿入されます。`adjm` は正方形で対称の行列でなければなりません。要素型 `T` は省略可能です。

## 例

```jldoctest
julia> using Graphs

julia> A1 = [false true; true false];

julia> SimpleGraph(A1)
{2, 1} undirected simple Int64 graph

julia> A2 = [2 7; 7 0];

julia> SimpleGraph{Int16}(A2)
{2, 2} undirected simple Int16 graph
```
