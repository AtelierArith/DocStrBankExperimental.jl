```
DensePredCG
```

`LinPred` 型で共役勾配法を用いた密な `X`

# メンバー

  * `X`: サイズ `n` × `p` のモデル行列で、`n ≥ p` である必要があります。完全列ランクであるべきです。
  * `beta0`: 長さ `p` の基準係数ベクトル
  * `delbeta`: 係数ベクトルへの増分で、長さ `p` でもあります
  * `scratchbeta`: 長さ `p` のスクラッチベクトルで、[`GLM.linpred!`](@ref) メソッドで使用されます
