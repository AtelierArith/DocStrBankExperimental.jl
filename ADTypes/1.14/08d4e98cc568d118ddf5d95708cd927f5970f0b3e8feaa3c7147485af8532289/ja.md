```
hessian_sparsity(f, x, sd::AbstractSparsityDetector)::AbstractMatrix{Bool}
```

検出器 `sd` を使用して、`x` に適用された `f` のヘッセ行列の非ゼロパターンを記述する（通常はスパースな）行列 `S` を構築します。
