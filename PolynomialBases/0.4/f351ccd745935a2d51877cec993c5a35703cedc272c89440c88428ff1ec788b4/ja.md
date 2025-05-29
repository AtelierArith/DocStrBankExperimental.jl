```
evaluate_coefficients!(xplot, uplot, u, basis::NodalBasis{Line})
```

ノーダル基底 `basis` の係数 `u` を `npoints` の等間隔ノードで評価し、結果を `xplot, uplot` に格納します。`xplot, uplot` を返し、`xplot` には等間隔ノードが含まれ、`uplot` には対応する `u` の値が含まれます。
