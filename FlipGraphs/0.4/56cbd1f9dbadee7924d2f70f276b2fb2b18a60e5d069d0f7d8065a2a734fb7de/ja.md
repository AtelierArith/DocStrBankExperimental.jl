```
distances(adjacency_matrix :: Matrix{T}) :: Matrix{T} where T<:Integer
```

与えられた `adjacency_matrix` に対して、任意の頂点から他の任意の頂点への最短距離を計算します。

`(i,j)` の位置にあるエントリが、`i` から `j` への最短経路の長さである `Matrix` を返します。

グラフは連結でなければなりません。このメソッドは *Seidels APSP-Algorithm* を使用します。
