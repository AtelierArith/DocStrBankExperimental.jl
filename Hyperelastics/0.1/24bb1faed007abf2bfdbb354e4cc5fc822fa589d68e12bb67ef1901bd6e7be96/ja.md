```julia
JamesGreenSimpson()
JamesGreenSimpson(type)

```

# モデル:

$$
W = \sum\limits_{i,j=0}^{3, 1}C_{i,j}(I_1-3)^i(I_2-3)^j
$$

# 引数:

  * `type=PrincipalValueForm()`: 応力エネルギー密度関数の形式を設定します。`PrincipalValueForm()` または `InvariantForm()` のいずれか

# パラメータ:

  * `C10`
  * `C01`
  * `C11`
  * `C20`
  * `C30`

> James AG, Green A, Simpson GM. ゴムのひずみエネルギー関数。I. ガムバルカニゼートの特性評価。応用ポリマー科学ジャーナル。1975年7月;19(7):2033-58.

