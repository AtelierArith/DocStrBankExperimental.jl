```
BackTracking(; autodiff = nothing, c_1 = 1e-4, ρ_hi = 0.5, ρ_lo = 0.1,
    order = 3,
    maxstep = Inf, initial_alpha = true)
```

`BackTracking` line search algorithm based on the implementation in [LineSearches.jl](https://github.com/JuliaNLSolvers/LineSearches.jl).

`BackTracking` specifies a backtracking line-search that uses a quadratic or cubic interpolant to determine the reduction in step-size.

E.g., if `f(α) > f(0) + c₁ α f'(0)`, then the quadratic interpolant of `f(0)`, `f'(0)`, `f(α)` has a minimiser `α'` in the open interval `(0, α)`. More strongly, there exists a factor ρ = ρ(c₁) such that `α' ≦ ρ α`.

This is a modification of the algorithm described in Nocedal Wright (2nd ed), Sec. 3.5.

`autodiff` is the automatic differentiation backend to use for the line search. This is only used for the derivative of the objective function at the current step size. `autodiff` must be specified if analytic jacobian/jvp/vjp is not available.
