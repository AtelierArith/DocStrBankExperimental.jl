```julia
KhiemItskov()
KhiemItskov(type)

```

# モデル:

$$
W = \mu_c \kappa n \log\bigg(\frac{\sin(\frac{\pi}{\sqrt{n}})(\frac{I_1}{3})^{\frac{q}{2}}}{\sin(\frac{\pi}{\sqrt{n}}(\frac{I_1}{3})^{\frac{q}{2}}}\bigg)+\mu_t\big[\frac{I_2}{3}^{1/2} - 1 \big]
$$

# 引数:

  * `type=PrincipalValueForm()`: ひずみエネルギー密度関数の形式を設定します。`PrincipalValueForm()` または `InvariantForm()` のいずれか。

# パラメータ:

  * μcκ
  * n
  * q
  * μt

> Khiêm VN, Itskov M. Analytical network-averaging of the tube model:: Rubber elasticity. Journal of the Mechanics and Physics of Solids. 2016年10月1日;95:254-69.

