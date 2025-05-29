```julia
Beatty()
Beatty(type)

```

# モデル:

$$
W = -\frac{G_0 I_m(I_m-3)}{2(2I_m-3)}\log\bigg(\frac{1-\frac{I_1-3}{I_m-3}}{1+\frac{I_1-3}{I_m}} \bigg)
$$

# 引数:

  * `type=PrincipalValueForm()`: ひずみエネルギー密度関数の形式を設定します。`PrincipalValueForm()` または `InvariantForm()` のいずれか。

# パラメータ:

  * `G₀`
  * `Iₘ`

> Beatty MF. 限定的弾性、分子ベースの材料のための構成モデルについて。数学と固体の力学。2008年7月;13(5):375-87.

