```julia
Lion()
Lion(type)

```

# モデル:

$$
W = \sum\limits_{i,j=0}^{5,1}C_{i,j}(I_1-3)^i(I_2-3)^j
$$

# 引数:

  * `type=PrincipalValueForm()`: 応力エネルギー密度関数の形式を設定します。`PrincipalValueForm()` または `InvariantForm()` のいずれか

# パラメータ:

  * `C10`
  * `C01`
  * `C50`

> Lion A. 異なる温度における強化ゴムの大変形挙動について。Journal of the Mechanics and Physics of Solids. 1997年11月1日;45(11-12):1805-34.

