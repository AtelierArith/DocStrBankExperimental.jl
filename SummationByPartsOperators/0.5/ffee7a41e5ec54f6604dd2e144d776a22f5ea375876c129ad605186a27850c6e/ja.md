```
evaluate_coefficients!(xplot, uplot, u, D::AbstractDerivativeOperator)
```

ノード係数 `u` を微分演算子 `D` に関連付けられたグリッドで評価し、結果を `xplot, uplot` に格納します。`xplot` にはノードが、`uplot` には対応する `u` の値が含まれた状態で `xplot, uplot` を返します。
