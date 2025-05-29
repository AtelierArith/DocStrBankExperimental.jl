```
simulate_derivatives_finite_difference(sequence, parameters)
```

`sequence` と `parameters` のみが提供されている場合、`echos` を計算し、その後、デフォルトのステップサイズを使用して非線形組織特性に関する `echos` の偏微分を有限差分法で計算します。`echos` と偏微分 `∂echos` の両方を返します。
