```julia
LambertDianiRey()
LambertDianiRey(type)

```

# モデル:

$$
W = \int\limits_{3}^{I_1}\exp\bigg(\sum\limits_{i=0}^{n}a_i(I_1-3)^i\bigg)\text{d}I_1+\int\limits_{3}^{I_2}\sum\limits_{j=0}^{m}b_i\log(I_2)^i\text{d}I_2
$$

# 引数:

  * `type=PrincipalValueForm()`: ひずみエネルギー密度関数の形式を設定します。`PrincipalValueForm()` または `InvariantForm()` のいずれか。

# パラメータ:

  * `a⃗`
  * `b⃗`

> Lambert-Diani J, Rey C. ゴムおよび熱可塑性エラストマーのための新しい現象論的挙動法則。European Journal of Mechanics-A/Solids. 1999年11月1日;18(6):1027-43.

