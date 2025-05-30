```
gamma_inc_minimax(a,x,z)
```

$$
P(a,x)
$$

を次のように与えられたミニマックス近似を使用して計算します：

$$
1/2 * \operatorname{erfc}(\sqrt{y}) - e^{-y}/\sqrt{2\pi a} ⋅ T(a,\lambda)
$$

ここで

$$
T(a,\lambda) = \sum_{0}^{N} c_{k}(z)a^{-k}
$$

これは、`a ≈ x`の近くで`a`が大きい領域を扱うTemme展開のより高精度な近似です。Brentの多倍長精度算術（50桁に設定）を使用して計算された係数の広範なセットについては、論文の付録Fを参照してください（[Brent (1978)](@cite brent_1978)）。

外部リンク: [DLMF 8.12.8](https://dlmf.nist.gov/8.12.8)

参照: [`gamma_inc(a,x,ind)`](@ref SpecialFunctions.gamma_inc) ```
