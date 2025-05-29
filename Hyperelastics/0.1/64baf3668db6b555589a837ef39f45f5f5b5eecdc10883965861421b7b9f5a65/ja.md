```julia
BechirChevalier(; ℒinv)

```

# モデル:

$$
W = W_{3Chain}(\mu_f, N_3)+W_{8Chain}(\frac{\mu_c}{3}, N_8)
$$

ここで:

$$
\mu_f = \rho\sqrt{\frac{I_1}{3N_8}}
$$

$$
\mu_c = \bigg(1-\frac{\eta\alpha}{\sqrt{N_3}}\bigg)\mu_0
$$

$$
\alpha = \max{\lambda_1, \lambda_2, \lambda_3}
$$

# 引数:

  * `ℒinv=TreloarApproximation()`: 使用される逆ランゲビン近似を設定します

# パラメータ:

  * `μ₀`
  * `η`
  * `ρ`
  * `N₃`
  * `N₈`

> Bechir H, Chevalier L, Idjeri M. ゴム弾性のための三次元ネットワークモデル: 局所的な絡みの制約の影響。国際工学科学ジャーナル。2010年3月1日;48(3):265-74.

