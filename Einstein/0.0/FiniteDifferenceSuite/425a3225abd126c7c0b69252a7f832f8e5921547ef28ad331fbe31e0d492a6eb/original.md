```
fdm_integrate_simpson(f::AbstractVector{T}, dx::T) where {T<:AbstractFloat}
```

Integrate a function `f` using Simpson's rule, given the grid spacing `dx`.
