```julia
AnsarriBenam(; ...)
AnsarriBenam(type; n)

```

# モデル:

$$
W = \frac{3(n-1)}{2n}\mu N \left[\frac{1}{3N(n-1)}(I_1 - 3) - \log{\frac{I_1 - 3N}{3 -3N}} \right]
$$

# 引数:

  * `type=PrincipalValueForm()`: ひずみエネルギー密度関数の形式を設定します。`PrincipalValueForm()` または `InvariantForm()` のいずれか
  * `ℒinv=TreloarApproximation()`: 使用する逆ランゲビン近似を設定します（デフォルト = ``）
  * `n::Int=3`: モデルの次数を設定します

# パラメータ:

  * `μ`
  * `n`
  * `N`

> Anssari-Benam A. On a new class of non-Gaussian molecular-based constitutive models with limiting chain extensibility for incompressible rubber-like materials. Mathematics and Mechanics of Solids. 2021 Nov;26(11):1660-74.

