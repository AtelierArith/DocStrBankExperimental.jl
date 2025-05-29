```julia
HartSmith()
HartSmith(type)

```

# モデル:

$$
W = \frac{G\exp{(-9k_1+k_1I_1)}}{k_1}+Gk_2\log{I_2}
$$

# 引数:

  * `type=PrincipalValueForm()`: ひずみエネルギー密度関数の形式を設定します。`PrincipalValueForm()` または `InvariantForm()` のいずれか。

# パラメータ:

  * `G`
  * `k₁`
  * `k₂`

> Hart-Smith LJ. ゴム様材料の有限変形に対する弾性パラメータ. Zeitschrift für angewandte Mathematik und Physik ZAMP. 1966年9月;17(5):608-26.

