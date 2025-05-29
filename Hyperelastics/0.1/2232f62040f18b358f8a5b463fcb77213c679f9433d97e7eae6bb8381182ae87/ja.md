```julia
ArrudaBoyce(; ...)
ArrudaBoyce(type; ℒinv)

```

# モデル:

$$
W = \mu N \left( \frac{\lambda_{chain}}{\sqrt{N}} \beta + \log\left(\frac{\beta}{\sinh\beta}\right) \right)
$$

ここで

$$
\beta = \mathcal{L}^{-1}\left(\frac{\lambda_{chain}}{\sqrt{N}}\right)
$$

および

$$
\lambda_{chain} = \sqrt{\frac{I_1}{3}}
$$

# 引数:

  * `type=PrincipalValueForm()`: ひずみエネルギー密度関数の形式を設定します。`PrincipalValueForm()` または `InvariantForm()` のいずれか
  * `ℒinv=TreloarApproximation()`: 使用される逆ランジュバン近似を設定します

# パラメータ:

  * `μ`: 小ひずみせん断弾性率
  * `N`: ネットワークのロッキングストレッチの二乗。

> Arruda EM, Boyce MC. A three-dimensional constitutive model for the large stretch behavior of rubber elastic materials. Journal of the Mechanics and Physics of Solids. 1993 Feb 1;41(2):389-412.

