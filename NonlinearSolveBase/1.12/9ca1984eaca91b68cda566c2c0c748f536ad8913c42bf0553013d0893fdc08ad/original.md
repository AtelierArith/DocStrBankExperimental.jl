```
SteepestDescent(; linsolve = nothing)
```

Compute the descent direction as $δu = -Jᵀfu$. The linear solver and preconditioner are only used if `J` is provided in the inverted form.

See also [`Dogleg`](@ref), [`NewtonDescent`](@ref), [`DampedNewtonDescent`](@ref).
