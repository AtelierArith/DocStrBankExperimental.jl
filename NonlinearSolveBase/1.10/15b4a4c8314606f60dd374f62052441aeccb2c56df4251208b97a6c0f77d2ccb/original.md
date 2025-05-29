```
NewtonDescent(; linsolve = nothing)
```

Compute the descent direction as $J δu = -fu$. For non-square Jacobian problems, this is commonly referred to as the Gauss-Newton Descent.

See also [`Dogleg`](@ref), [`SteepestDescent`](@ref), [`DampedNewtonDescent`](@ref).
