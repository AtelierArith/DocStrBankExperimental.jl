```
GenericCriteria
```

This is a generic convergence criteria that uses:

1. The maximum change in the solution, `Δx`,
2. The change in the objective value, `Δf`, and
3. The change percentage in the objective value, `Δf`, and
4. The maximum infeasibility `infeas`.

to assess convergence. More details are given in [`assess_convergence!`](@ref).
