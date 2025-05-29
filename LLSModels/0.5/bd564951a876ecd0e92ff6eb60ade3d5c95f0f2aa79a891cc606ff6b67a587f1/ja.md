```
nls = LLSModel(A, b; lvar, uvar, C, lcon, ucon)
```

線形最小二乗モデル $\tfrac{1}{2}\|Ax - b\|^2$ を作成します。オプションの境界 `lvar ≦ x ≦ uvar` とオプションの線形制約 `lcon ≦ Cx ≦ ucon` があります。この問題は、残差が $F(x) = Ax - b$ である非線形最小二乗問題です。
