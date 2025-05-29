```
EisenstatWalkerForcing(;
    initial_rtol = 0.5,
    γ = 1,
    α = 2,
    min_rtol_threshold = 0.1,
    max_rtol = 0.9,
)
```

The `ForcingTerm` called "Choice 2" in the paper "Choosing the Forcing Terms in an Inexact Newton Method" by S.C. Eisenstat and H.F. Walker. The values of `initial_rtol`, `min_rtol_threshold`, and `max_rtol` must be in the interval `[0, 1)`, the value of `γ` must be in the interval `[0, 1]`, and the value of `α` must be in the interval `(1, 2]`. These values can all be tuned to prevent the Newton-Krylov method from oversolving. If `x` and `f!` satisfy certain assumptions, this forcing term guarantees that the Newton-Krylov method will converge with order `α`. Note that, although a larger value of `α` guarantees a higher convergence order, it also leads to a higher probability of oversolving.

This forcing term was implemented instead of the one called "Choice 1" because it has a significantly simpler implementation–-it only requires the value of `‖f(x[n])‖` to compute `rtol[n]`, whereas "Choice 1" also requires the norm of the final residual from the Krylov solver.
