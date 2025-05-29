```julia
Swanson()
Swanson(type)

```

# モデル:

$$
W = \sum\limits_{i=1}^{N} \frac{3}{2}(\frac{A_i}{1+\alpha_i}(\frac{I_1}{3})^{1+\alpha_i}+\frac{B_i}{1+\beta_i}(\frac{I_2}{3})^{1+\beta_i}
$$

# 引数:

  * `type=PrincipalValueForm()`: ひずみエネルギー密度関数の形式を設定します。`PrincipalValueForm()` または `InvariantForm()` のいずれか。

# パラメータ:

  * `A⃗`
  * `α⃗`
  * `B⃗`
  * `β⃗`

> Swanson SR. 高伸長弾性材料のための構成モデル。

