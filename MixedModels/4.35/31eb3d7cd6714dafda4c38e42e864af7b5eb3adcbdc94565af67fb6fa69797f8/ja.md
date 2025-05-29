```
BlockedSparse{Tv,S,P}
```

行または列、またはその両方のブロックを形成する非ゼロ要素を持つ `SparseMatrixCSC`。

# メンバー

  * `cscmat`: 一般的な計算のための `SparseMatrixCSC{Tv, Int32}` 表現
  * `nzasmat`: 密行列としての `cscmat` の非ゼロ要素
  * `colblkptr`: 列のブロックのパターン

これらが作成されるのは、`ReMat` の積としてのみです。
