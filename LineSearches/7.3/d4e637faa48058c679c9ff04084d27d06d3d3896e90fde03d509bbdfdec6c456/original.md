```
(ls::StrongWolfe)(df, x::AbstractArray, p::AbstractArray, alpha0::Real, x_new, ϕ_0, dϕ_0) -> alpha, ϕalpha
```

Given a differentiable function `df` (in the sense of `NLSolversBase.OnceDifferentiable` or `NLSolversBase.TwiceDifferentiable`), a multidimensional starting point `x` and step `p`, and a guess `alpha0` for the step length, find an `alpha` satisfying the strong Wolfe conditions.

See the one-dimensional method for additional details.
