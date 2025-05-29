```
IndexedDiGraph{T<:Integer} <: AbstractIndexedDiGraph{T}
```

出辺のみにアクセスできる疎有向グラフを表す型です。

### フィールド

  * `A` – `NullNumber` で埋められた正方行列。`A[i,j]` は辺 `j=>i` に対応します。
