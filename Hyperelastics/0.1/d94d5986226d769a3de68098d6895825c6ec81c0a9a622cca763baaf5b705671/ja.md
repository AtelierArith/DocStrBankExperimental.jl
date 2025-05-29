```julia
PucciSaccomandi()
PucciSaccomandi(type)

```

# モデル:

$$
W = K\log{\frac{I_2}{3}}-\frac{\mu J_m}{2}\log{1-\frac{I_1-3}{J-m}}
$$

# 引数:

  * `type=PrincipalValueForm()`: ひずみエネルギー密度関数の形式を設定します。`PrincipalValueForm()` または `InvariantForm()` のいずれか。

# パラメータ:

  * `K`
  * `μ`
  * `Jₘ`

> Pucci E, Saccomandi G. ゴムのような材料のためのGentモデルに関するノート。ゴム化学と技術。2002年11月;75(5):839-52.

