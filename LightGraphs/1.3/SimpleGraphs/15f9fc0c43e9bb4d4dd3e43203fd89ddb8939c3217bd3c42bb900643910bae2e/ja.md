```
SimpleGraph{T}(adjm::AbstractMatrix)
```

隣接行列 `adjm` から `SimpleGraph{T}` を構築します。もし `adjm[i][j] != 0` であれば、辺 `(i, j)` が挿入されます。`adjm` は正方行列で対称でなければなりません。要素型 `T` は省略可能です。

## 例

```jldoctest
julia> A1 = [false true; true false]
julia> SimpleGraph(A1)
{2, 1} 無向単純 Int64 グラフ

julia> A2 = [2 7; 7 0]
julia> SimpleGraph{Int16}(A2)
{2, 2} 無向単純 Int16 グラフ
```
