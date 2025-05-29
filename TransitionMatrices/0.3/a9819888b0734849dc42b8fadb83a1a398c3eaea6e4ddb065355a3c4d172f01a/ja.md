```
expansion_coefficients(𝐓::AxisymmetricTransitionMatrix{CT, N, V, T}, λ) where {CT, N, V, T}
```

軸対称T行列から展開係数を計算します。MishchenkoらのFortranコードから翻訳されました。

パラメータ：

  * `𝐓`: 散乱体の事前計算されたT行列。
  * `λ`: 波長。
