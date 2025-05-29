```
IndexedBiDiGraph{T<:Integer} <: AbstractIndexedDiGraph{T}
```

出力辺と入力辺の両方にアクセスできる疎有向グラフを表す型です。

### フィールド

  * `A` – `NullNumber` で埋められた正方行列。 `A[i,j]` は辺 `j=>i` に対応します。
  * `X` – 行による効率的なアクセスのための正方行列。 `X[j,i]` は `A.nzval` における要素 `A[i,j]` のインデックスを指します。
