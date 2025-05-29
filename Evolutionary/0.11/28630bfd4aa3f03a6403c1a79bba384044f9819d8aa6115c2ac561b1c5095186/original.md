```
isfeasible(bounds::ConstraintBounds, x) -> Bool
```

Return `true` if point `x` is feasible, given the `bounds` object with bounds `lx`, `ux`, `lc`, and `uc`. `x` is feasible if

```
lx[i] <= x[i] <= ux[i]
lc[i] <= c(x)[i] <= uc[i]
```

for all possible `i`.
