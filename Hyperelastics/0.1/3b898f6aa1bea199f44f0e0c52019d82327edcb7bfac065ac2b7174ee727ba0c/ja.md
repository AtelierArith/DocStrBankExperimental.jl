```julia
ModifiedYeoh()
ModifiedYeoh(type)

```

# モデル:

$$
W = C_{10} * (I_1 - 3) + C_{20} * (I_1 - 3)^2 + C_{30} * (I_1 - 3)^3 + \alpha / \beta * (1 - \exp{-\beta * (I_1 - 3)})
$$

# 引数:

  * `type=PrincipalValueForm()`: ひずみエネルギー密度関数の形式を設定します。`PrincipalValueForm()` または `InvariantForm()` のいずれかです。

# パラメータ:

  * `C10`
  * `C20`
  * `C30`
  * `α`
  * `β`

> He H, Zhang Q, Zhang Y, Chen J, Zhang L, Li F. A comparative study of 85 hyperelastic constitutive models for both unfilled rubber and highly filled rubber nanocomposite material. Nano Materials Science. 2021 Jul 16.

