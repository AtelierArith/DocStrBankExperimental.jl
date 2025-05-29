```
StopWhenKKTResidualLess <: StoppingCriterion
```

KKT残差が少なくなったときに停止します

```
r^2
= \lVert \operatorname{grad}_p \mathcal L(p, μ, λ) \rVert^2
+ \sum_{i=1}^m [μ_i]_{-}^2 + [g_i(p)]_+^2 + \lvert \mu_ig_i(p)^2
+ \sum_{j=1}^n \lvert h_i(p)\rvert^2.
```

が与えられた閾値 $r < ε$ より小さい場合。ここで、$[v]_+ = \max\{0,v\}$ および $[v]_- = \min\{0,t\}$ はそれぞれ $v$ の正の部分と負の部分を表します。

# フィールド

  * `ε`: 閾値
  * `at_iteration`:
