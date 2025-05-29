```julia
ExpLn()
ExpLn(type)

```

# モデル:

$$
W = A\bigg[\frac{1}{a}\exp{(a(I_1-3))}+b(I_1-2)(1-\log{I_1-2})-\frac{1}{a}-b\bigg]
$$

# 引数:

  * `type=PrincipalValueForm()`: ひずみエネルギー密度関数の形式を設定します。`PrincipalValueForm()` または `InvariantForm()` のいずれか。

# パラメータ:

  * `A`
  * `a`
  * `b`

> Khajehsaeid H, Arghavani J, Naghdabadi R. ゴムのような材料のための超弾性構成モデル。European Journal of Mechanics-A/Solids. 2013年3月1日;38:144-51.

