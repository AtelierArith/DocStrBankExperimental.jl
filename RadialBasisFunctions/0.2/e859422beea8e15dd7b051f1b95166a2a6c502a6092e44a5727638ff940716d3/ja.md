```
function ∂virtual(data, eval_points, dim, Δ, basis; k=autoselect_k(data, basis))
```

`eval_points` で評価される仮想 `RadialBasisOperator` を構築します。この演算子は `dim` に関する偏導関数です。仮想演算子は、標準的な有限差分公式を適用できる距離 `Δ` の構造化された点にデータを補間します。
