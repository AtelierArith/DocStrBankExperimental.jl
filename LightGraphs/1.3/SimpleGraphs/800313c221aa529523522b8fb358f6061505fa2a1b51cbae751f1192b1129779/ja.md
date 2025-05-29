```
SimpleDiGraph{T}(adjm::AbstractMatrix)
```

隣接行列 `adjm` から `SimpleDiGraph{T}` を構築します。もし `adjm[i][j] != 0` であれば、エッジ `(i, j)` が挿入されます。`adjm` は正方行列でなければなりません。要素型 `T` は省略可能です。

## 例

```jldoctest
julia> A1 = [false true; false false]
julia> SimpleDiGraph(A1)
{2, 1} directed simple Int64 graph

julia> A2 = [2 7; 5 0]
julia> SimpleDiGraph{Int16}(A2)
{2, 3} directed simple Int16 graph
```
