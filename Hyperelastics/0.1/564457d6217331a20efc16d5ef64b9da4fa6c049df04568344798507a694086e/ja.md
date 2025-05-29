```julia
DavisDeThomas()
DavisDeThomas(type)

```

# モデル:

$$
W = \frac{A}{2(1-\frac{n}{2})}(I_1-3+C^2)^{1-\frac{n}{2}}+k(I_1-3)^2
$$

# 引数

  * `type=PrincipalValueForm()`: 応力エネルギー密度関数の形式を設定します。`PrincipalValueForm()` または `InvariantForm()` のいずれか。

# パラメータ:

  * `A`
  * `n`
  * `C`
  * `k`

> Davies CK, De DK, Thomas AG. 工学設計目的のためのゴムの挙動の特性評価。1. 応力-ひずみ関係。ゴム化学と技術。1994年9月;67(4):716-28.

