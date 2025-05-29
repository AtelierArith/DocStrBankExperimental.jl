```
evaluate_coefficients(u, basis::NodalBasis{Line}, npoints=2*length(basis.nodes))
```

ノーダル基底 `basis` の係数 `u` を `npoints` の等間隔ノードで評価します。`xplot, uplot` を返し、`xplot` には等間隔ノードが含まれ、`uplot` には対応する `u` の値が含まれます。
