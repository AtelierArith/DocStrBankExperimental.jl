```
count_exog_points(p::Plan, rng, vars)
```

Count the number of exogenous points for the given plan over the given range.

Example:

```
count_exog_points(p, :, m.exogenous)
```

See also [`count_endo_points`](@ref)
