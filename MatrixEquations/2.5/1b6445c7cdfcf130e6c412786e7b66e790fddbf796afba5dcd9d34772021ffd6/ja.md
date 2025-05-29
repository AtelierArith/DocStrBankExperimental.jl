```
L = lyaplikeop(A; isig = 1, adj = false, htype = false)
```

行列 `A` に対して、`adj = false` の場合、連続 T-リャプノフ演算子 `L:X -> A*X+isig*transpose(X)*transpose(A)` を定義します。`htype = false` の場合、または連続 H-リャプノフ演算子 `L:X -> A*X+isig*X'*A'` を定義します。`htype = true` の場合、または `adj = true` の場合、連続 T-リャプノフ演算子 `L:X -> A*transpose(X)+X*transpose(A)` を定義します。`htype = false` の場合、または連続 H-リャプノフ演算子 `L:X -> A*X'+isig*X*A'` を定義します。`htype = true` の場合。
