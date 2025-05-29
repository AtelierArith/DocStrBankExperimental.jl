```
AbstractIndexedGraph{T} <: AbstractGraph{T}
```

インデックス付きグラフを表す抽象型です。`AbstractIndexedGraph`は以下の要素を持たなければなりません：

  * `A::SparseMatrixCSC` 隣接行列
