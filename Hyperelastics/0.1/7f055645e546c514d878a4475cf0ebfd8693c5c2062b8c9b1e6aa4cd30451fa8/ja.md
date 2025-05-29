```julia
Beda()
Beda(type)

```

# モデル:

$$
W = \frac{C_1}{\alpha}(I_1-3)^{\alpha}+C_2(I_1-3)+\frac{C_3}{\zeta}(I_1-3)^{\zeta}+\frac{K_1}{\beta}(I_2-3)^\beta
$$

# 引数:

  * `type=PrincipalValueForm()`: ひずみエネルギー密度関数の形式を設定します。`PrincipalValueForm()` または `InvariantForm()` のいずれかです。

# パラメータ:

  * `C1`
  * `C2`
  * `C3`
  * `K1`
  * `α`
  * `β`
  * `ζ`

> Beda T. ゴムのひずみエネルギーの基本的な現象論的表現を確立された実験事実と調和させる。ポリマー科学ジャーナルB: ポリマーフィジックス。2005年1月15日;43(2):125-34.

