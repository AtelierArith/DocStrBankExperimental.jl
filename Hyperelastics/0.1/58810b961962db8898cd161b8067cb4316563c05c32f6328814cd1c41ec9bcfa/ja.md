```julia
GenYeoh()
GenYeoh(type)

```

# モデル:

$$
W = K_1 (I_1 - 3)^m + K_2 * (I_1 - 3)^p + K_3 * (I_1 - 3)^q
$$

# 引数:

  * `type=PrincipalValueForm()`: ひずみエネルギー密度関数の形式を設定します。`PrincipalValueForm()` または `InvariantForm()` のいずれか。

# パラメータ:

  * `K1`
  * `K2`
  * `K3`
  * `m`
  * `p`
  * `q`

> Hohenberger TW, Windslow RJ, Pugno NM, Busfield JJ. A constitutive model for both low and high strain nonlinearities in highly filled elastomers and implementation with user-defined material subroutines in ABAQUS. Rubber Chemistry and Technology. 2019;92(4):653-86.

