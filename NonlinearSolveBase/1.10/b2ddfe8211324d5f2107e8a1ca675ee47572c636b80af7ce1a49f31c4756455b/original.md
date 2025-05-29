```
Dogleg(; linsolve = nothing)
```

Switch between Newton's method and the steepest descent method depending on the size of the trust region. The trust region is specified via keyword argument `trust_region` to `solve!`.

See also [`SteepestDescent`](@ref), [`NewtonDescent`](@ref), [`DampedNewtonDescent`](@ref).
