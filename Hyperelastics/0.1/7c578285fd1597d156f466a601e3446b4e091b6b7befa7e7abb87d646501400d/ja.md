```julia
HainesWilson()
HainesWilson(type)

```

# モデル:

$$
W = \sum\limits_{i,j=0}^{3, 2}C_{i,j}(I_1-3)^i(I_2-3)^j
$$

# 引数:

  * `type=PrincipalValueForm()`: 応力エネルギー密度関数の形式を設定します。`PrincipalValueForm()`または`InvariantForm()`のいずれか

# パラメータ:

  * `C10`
  * `C01`
  * `C11`
  * `C02`
  * `C20`
  * `C30`

> Haines DW, Wilson WD. ゴム状材料のためのひずみエネルギー密度関数. Journal of the Mechanics and Physics of Solids. 1979年8月1日;27(4):345-60.

