```
evaluate_coefficients(u, D::AbstractDerivativeOperator)
```

ノード係数 `u` を微分演算子 `D` に関連付けられたグリッドで評価します。`xplot, uplot` を返し、`xplot` にはノードが含まれ、`uplot` には `u` の対応する値が含まれます。
