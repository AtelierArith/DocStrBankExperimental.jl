```
L = hulyaplikeop(U; adj = false)
```

上三角行列 `U` に対して、連続 H-Lyapunov 演算子 `L:X -> U'*X+X'*U` を定義します。`adj = false` の場合、`L:X -> U*X'+X*U'` となります。
