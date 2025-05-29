```julia
Lim(; ...)
Lim(type; ℒinv)

```

# モデル:

$$
W = \left(1-f\left(\frac{I_1-3}{\hat{I_1}-3}\right)\right)W_{NeoHookean}(μ₁)+fW_{ArrudaBoyce}(μ₂, N)
$$

# 引数:

  * `type=PrincipalValueForm()`: ひずみエネルギー密度関数の形式を設定します。`PrincipalValueForm()` または `InvariantForm()`
  * `ℒinv=TreloarApproximation()`: 使用される逆ランゲビン近似を設定します

# パラメータ:

  * `μ₁`
  * `μ₂`
  * `N`
  * `Î₁`

> Lim GT. ポリマーの引っかき挙動. テキサスA&M大学; 2005.

