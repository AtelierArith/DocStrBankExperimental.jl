```julia
HossMarczakII()
HossMarczakII(type)

```

# モデル:

$$
W = \frac{\alpha}{\beta}(1-\exp{-\beta(I_1-3)})+\frac{\mu}{2b}\bigg((1+\frac{b}{n}(I_1-3))^n -1\bigg)+C_2\log(\frac{I_2}{3})
$$

# 引数:

  * `type=PrincipalValueForm()`: ひずみエネルギー密度関数の形式を設定します。`PrincipalValueForm()` または `InvariantForm()` のいずれか。

# パラメータ:

  * `α`
  * `β`
  * `μ`
  * `b`
  * `n`
  * `C2`

# 注意:

  * 著者はこのモデルを高ひずみに対して提案しています。

> Hoss L, Marczak RJ. A new constitutive model for rubber-like materials. Mecánica Computacional. 2010;29(28):2759-73.

