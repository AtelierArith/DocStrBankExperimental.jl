```
count_endo_points(p::Plan, rng, vars)
```

与えられた範囲に対する与えられたプランの内生的ポイントの数をカウントします。

例:

```
count_endo_points(p, :, m.shocks)
```

また、[`count_exog_points`](@ref)も参照してください。
