```
FluxRotated(numerical_flux)
```

Compute a `numerical_flux` flux in direction of a normal vector by rotating the solution, computing the numerical flux in x-direction, and rotating the calculated flux back.

Requires a rotationally invariant equation with equation-specific functions [`rotate_to_x`](@ref) and [`rotate_from_x`](@ref).
