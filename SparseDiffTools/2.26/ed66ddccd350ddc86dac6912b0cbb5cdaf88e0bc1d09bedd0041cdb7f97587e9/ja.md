```
matrix_colors(A, alg::ColoringAlgorithm = GreedyD1Color();
    partition_by_rows::Bool = false)
```

行列 A の色ベクトルを選択した着色アルゴリズムを使用して返します。既知の解析的解が存在する場合、それが代わりに使用されます。着色はデフォルトで貪欲な距離-1 着色になります。

A が SparseMatrixCSC の場合、スパースパターンは構造的非ゼロによって定義され、明示的に保存されたゼロを含みます。

`ArrayInterface.fast_matrix_colors(A)` が true の場合、`ArrayInterface.matrix_colors(A)` を使用して行列の色を計算します。
