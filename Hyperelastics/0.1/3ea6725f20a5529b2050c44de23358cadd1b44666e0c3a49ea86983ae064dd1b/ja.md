```julia
ABGI(; ℒinv)

```

# モデル:

$$
W = W_{Arruda-Boyce} + \frac{G_e}{n} \left(\sum_{i=1}^{3}\lambda_i^n-3\right)
$$

# 引数:

  * `ℒinv = TreloarApproximation()`: 使用する逆ランジュバン近似を設定します (デフォルト = `TreloarApproximation()`)

# パラメータ:

  * `μ`
  * `N`
  * `Ge`
  * `n`

> Meissner B, Matějka L. ゴム状ネットワークのためのランジュバン弾性理論に基づく構成方程式とその二軸応力-ひずみデータとの比較。第I部。ポリマー。2003年7月1日;44(16):4599-610.

