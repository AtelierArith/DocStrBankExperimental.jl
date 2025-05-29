```julia
LopezPamies()
LopezPamies(type)

```

# モデル:

$$
W = \frac{3^{1 - \alpha_i}}{2\alpha_i} \mu_i (I_1^{\alpha_i} - 3^{\alpha_i})
$$

# 引数:

  * `type=PrincipalValueForm()`: ひずみエネルギー密度関数の形式を設定します。`PrincipalValueForm()` または `InvariantForm()` のいずれか。

# パラメータ:

  * `α⃗`
  * `μ⃗`

> Lopez-Pamies O. 新しいI1ベースのハイパーエラスティックモデルをゴム弾性材料に対して提案します。Comptes Rendus Mecanique. 2010年1月1日;338(1):3-11.

