```julia
Isihara()
Isihara(type)

```

# モデル:

$$
W = \sum\limits_{i,j=0}^{2, 1}C_{i,j}(I_1-3)^i(I_2-3)^j
$$

# 引数:

  * `type=PrincipalValueForm()`: 応力エネルギー密度関数の形式を設定します。`PrincipalValueForm()` または `InvariantForm()` のいずれか

# パラメータ:

  * `C10`
  * `C20`
  * `C01`

> Isihara A, Hashitsume N, Tatibana M. ゴム様弾性の統計理論。IV.（二次元の伸び）。化学物理学ジャーナル。1951年12月;19(12):1508-12.

