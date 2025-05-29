```
count_exog_points(p::Plan, rng, vars)
```

与えられた範囲に対する指定されたプランの外生点の数をカウントします。

例:

```
count_exog_points(p, :, m.exogenous)
```

関連情報として [`count_endo_points`](@ref) を参照してください。
