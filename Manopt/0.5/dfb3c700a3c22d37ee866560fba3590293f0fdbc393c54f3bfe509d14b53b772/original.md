```
StopWhenKKTResidualLess <: StoppingCriterion
```

Stop when the KKT residual

```
r^2
= \lVert \operatorname{grad}_p \mathcal L(p, μ, λ) \rVert^2
+ \sum_{i=1}^m [μ_i]_{-}^2 + [g_i(p)]_+^2 + \lvert \mu_ig_i(p)^2
+ \sum_{j=1}^n \lvert h_i(p)\rvert^2.
```

is less than a given threshold $r < ε$. We use $[v]_+ = \max\{0,v\}$ and $[v]_- = \min\{0,t\}$ for the positive and negative part of $v$, respectively

# Fields

  * `ε`: a threshold
  * `residual`: store the last residual if the stopping criterion is hit.
  * `at_iteration`:
