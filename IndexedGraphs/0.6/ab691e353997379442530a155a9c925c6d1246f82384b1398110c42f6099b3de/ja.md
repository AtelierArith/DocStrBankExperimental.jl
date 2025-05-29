```
IndexedGraph{T<:Integer} <: AbstractIndexedGraph{T}
```

疎な無向グラフを表す型です。

### フィールド

  * `A` – 正方形の隣接行列。`A[i,j] == A[j,i]` は無向辺 `(i,j)` に関連付けられたユニークなインデックスを含みます。
