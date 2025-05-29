```
count_endo_points(p::Plan, rng, vars)
```

Count the number of endogenous points for the given plan over the given range.

Example:

```
count_endo_points(p, :, m.shocks)
```

See also [`count_exog_points`](@ref)
