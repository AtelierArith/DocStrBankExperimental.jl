```
schur_stab(A::AbstractMatrix{T}, ϵ = 0.01)
```

離散時間行列 `A` の固有値を安定化するために、`A` を複素シュル形式に変換し、不安定な固有値 1-ϵ < λ ≤ 2 を単位円に射影します。固有値が 2 を超える場合は 0 に設定されます。
