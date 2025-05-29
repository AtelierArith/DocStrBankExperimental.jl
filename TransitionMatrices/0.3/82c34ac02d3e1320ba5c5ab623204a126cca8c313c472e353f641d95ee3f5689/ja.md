```
expansion_coefficients(𝐓::AbstractTransitionMatrix{CT, N}, λ) where {CT, N}
```

任意のT行列から展開係数を計算します。Bi et al. (2014)の式(24) – (74)を使用します。

パラメータ:

  * `𝐓`: 散乱体の事前計算されたT行列。
  * `λ`: 波長。

キーワード引数:

  * `full`: 完全な展開係数（`β₃`から`β₆`）を返すかどうか。デフォルトは`false`です。
