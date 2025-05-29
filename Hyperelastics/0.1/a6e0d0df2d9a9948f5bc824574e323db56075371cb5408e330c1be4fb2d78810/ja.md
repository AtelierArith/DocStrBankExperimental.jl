```julia
ThreeChainModel(; ℒinv)

```

# モデル:

$$
W = \frac{\mu\sqrt{N}}{3}\sum\limits_{i=1}^{3}\bigg(\lambda_i\beta_i+\sqrt{N}\log\bigg(\frac{\beta_i}{\sinh \beta_i}\bigg)\bigg)
$$

# 引数:

  * `ℒinv=TreloarApproximation()`: 使用する逆ランジュバン近似を設定します

# パラメータ:

  * `μ`: 小ひずみせん断弾性率
  * `N`: ネットワークのロッキングストレッチの二乗。

> James HM, Guth E. ゴムの弾性特性の理論. The Journal of Chemical Physics. 1943年10月;11(10):455-81.

