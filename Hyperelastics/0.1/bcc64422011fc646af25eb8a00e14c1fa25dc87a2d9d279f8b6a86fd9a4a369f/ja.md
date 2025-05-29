```julia
VerondaWestmann()
VerondaWestmann(type)

```

# モデル:

$$
W = C_1 (\exp(\alpha(I_1 - 3)) - 1) + C_2 (I_2 - 3)
$$

# 引数:

  * `type=PrincipalValueForm()`: 応力エネルギー密度関数の形式を設定します。`PrincipalValueForm()` または `InvariantForm()` のいずれか。

# パラメータ:

  * `C1`
  * `C2`
  * `α`

> Veronda DR, Westmann RA. Mechanical characterization of skin—finite deformations. Journal of biomechanics. 1970 Jan 1;3(1):111-24.

