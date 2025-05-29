```
jacobian_sparsity(f, x, sd::AbstractSparsityDetector)::AbstractMatrix{Bool}
jacobian_sparsity(f!, y, x, sd::AbstractSparsityDetector)::AbstractMatrix{Bool}
```

検出器 `sd` を使用して、`f`（または `f!`）が `x`（または `(y, x)`）に適用されたときのヤコビ行列の非ゼロパターンを記述する（通常はスパースな）行列 `S` を構築します。
