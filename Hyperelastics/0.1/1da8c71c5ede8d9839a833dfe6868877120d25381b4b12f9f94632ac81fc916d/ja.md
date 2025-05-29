```julia
ConstrainedJunction()

```

# モデル:

$$
W = G_c (I_1-3)+ \frac{\nu k T}{2}\left(\sum\limits_{i=1}^{3}\kappa\frac{\lambda_i-1}{\lambda_i^2+\kappa}+\log{\frac{\lambda_i^2+\kappa}{1+\kappa}}-\log{\lambda_i^2}\right)
$$

# パラメータ:

  * `Gc`
  * `νkT`
  * `κ`

> Flory PJ, Erman B. ポリマー網の弾性に関する理論. 3. マクロ分子. 1982年5月;15(3):800-6. Erman B, Flory PJ. ポリマー網の応力、ひずみ、および分子構成の関係. 理論と実験の比較. マクロ分子. 1982年5月;15(3):806-11.

