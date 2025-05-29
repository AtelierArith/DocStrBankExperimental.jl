```julia
HauptSedlan()
HauptSedlan(type)

```

# モデル:

$$
W = \sum\limits_{i,j=0}^{3, 2}C_{i,j}(I_1-3)^i(I_2-3)^j
$$

# 引数:

  * `type=PrincipalValueForm()`: 応力エネルギー密度関数の形式を設定します。`PrincipalValueForm()` または `InvariantForm()` のいずれか

# パラメータ:

  * `C10`
  * `C01`
  * `C11`
  * `C02`
  * `C30`

> Haupt P, Sedlan K. Viscoplasticity of elastomeric materials: experimental facts and constitutive modelling. Archive of Applied Mechanics. 2001 Mar;71(2):89-109.

