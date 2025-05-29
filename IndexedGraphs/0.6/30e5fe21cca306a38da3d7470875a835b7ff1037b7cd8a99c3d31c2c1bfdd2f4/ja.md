```
IndexedDiGraph(A::AbstractMatrix)
```

隣接行列 A から IndexedDiGraph を構築します。

`IndexedDiGraph` は内部的に `A` の転置を保存します。転置によるオーバーヘッドを避けるために、`IndexedDiGraph(transpose(At))` を使用してください。ここで `At` は `A` の転置です。
