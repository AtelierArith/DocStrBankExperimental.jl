```
IndexedBiDiGraph(A::AbstractMatrix)
```

隣接行列 `A` から `IndexedBiDiGraph` を構築します。

`IndexedBiDiGraph` は内部的に `A` の転置を保存します。転置によるオーバーヘッドを避けるために、`At` が `A` の転置である場合は `IndexedBiDiGraph(transpose(At))` を使用してください。
