```
sparspaklu!(lu::SparseSolver, m::SparseMatrixCSC; allow_pattern_change=true) -> lu::SparseSolver
```

スパース行列 `m` のLU因子分解を計算し、以前に計算された場合は、順序付けと象徴的因子分解 `lu` を再利用します。

`allow_pattern_change = true`（デフォルト）である場合、スパース行列 `m` はLU因子分解 `lu` を作成するために使用された行列とは異なる非ゼロパターンを持つ可能性があり、その場合、順序付けと象徴的因子分解が更新されます。

`allow_pattern_change = false` の場合、`m` の非ゼロパターンがLU因子分解 `lu` を作成するために使用された行列と異なるとエラーが発生します。

`lu` が因子分解されていない場合（つまり、オプション `factorize = false` で作成された場合）、`lu` は常に `m` から更新され、`allow_pattern_change` は無視されます。
