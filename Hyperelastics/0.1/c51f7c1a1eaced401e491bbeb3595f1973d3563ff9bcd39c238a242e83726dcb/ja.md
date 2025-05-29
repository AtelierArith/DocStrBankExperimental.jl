```julia
Gent()
Gent(type)

```

# モデル:

$$
W = -\frac{\mu J_m}{2}\log{\bigg(1-\frac{I_1-3}{J_m}\bigg)}
$$

# 引数:

  * `type=PrincipalValueForm()`: ひずみエネルギー密度関数の形式を設定します。`PrincipalValueForm()` または `InvariantForm()` のいずれか。

# パラメータ:

  * `μ`: 小ひずみせん断弾性率
  * `Jₘ`: 限界伸び不変量

> Gent AN. ゴムのための新しい構成関係。ゴム化学と技術。1996年3月;69(1):59-61.

