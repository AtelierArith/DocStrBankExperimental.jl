```
Y = get_hessian(amp::AbstractManoptProblem{T}, p, X)
get_hessian!(amp::AbstractManoptProblem{T}, Y, p, X)
```

evaluate the Hessian of an [`AbstractManoptProblem`](@ref) `amp` at `p` applied to a tangent vector `X`, computing $\operatorname{Hess}f(q)[X]$, which can also happen in-place of `Y`.
