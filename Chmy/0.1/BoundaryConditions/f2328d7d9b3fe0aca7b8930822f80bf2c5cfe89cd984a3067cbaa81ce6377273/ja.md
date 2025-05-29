```
bc!(arch::Architecture, grid::StructuredGrid, batch::BatchSet)
```

バッチセット `batch` を使用して、`grid` の各次元の各側に対して `AbstractBatch` を含む境界条件を適用します。

# 引数

  * `arch`: アーキテクチャ。
  * `grid`: グリッド。
  * `batch:`: 境界条件を適用するバッチセット。
