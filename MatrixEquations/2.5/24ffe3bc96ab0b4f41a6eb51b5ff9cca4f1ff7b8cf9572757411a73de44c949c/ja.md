```
L = tulyaplikeop(U; adj = false)
```

上三角行列 `U` に対して、連続 T-リャプノフ演算子 `L:X -> transpose(U)*X+transpose(X)*U` を定義します。`adj = false` の場合、または `L:X -> U*transpose(X)+X*transpose(U)` を定義します。`adj = true` の場合。
