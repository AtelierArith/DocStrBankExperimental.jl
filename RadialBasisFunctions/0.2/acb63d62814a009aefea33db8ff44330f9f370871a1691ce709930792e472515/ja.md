```
function ∂virtual(data, dim, Δ, basis; k=autoselect_k(data, basis))
```

入力点（`data`）で評価される仮想の `RadialBasisOperator` を構築します。この演算子は `dim` に関する偏微分です。仮想演算子は、標準的な有限差分公式を適用できる距離 `Δ` の構造化された点にデータを補間します。
