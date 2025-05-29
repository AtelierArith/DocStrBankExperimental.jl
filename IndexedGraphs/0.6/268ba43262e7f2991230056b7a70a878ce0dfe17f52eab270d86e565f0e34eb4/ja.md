```
BipartiteIndexedGraph{T<:Integer} <: AbstractIndexedGraph{T}
```

疎な無向二部グラフを表す型です。

### フィールド

  * `A` – `NullNumber` で埋められた隣接行列。行は左ブロックに属する頂点、列は右ブロックに属します。
  * `X` – 行による効率的なアクセスのための正方行列。`X[j,i]` は `A.nzval` における要素 `A[i,j]` のインデックスを指します。
