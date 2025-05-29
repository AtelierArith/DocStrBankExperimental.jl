```
FluxUpwind(splitting)
```

A numerical flux `f(u_left, u_right) = f⁺(u_left) + f⁻(u_right)` based on flux vector splitting.

The [`SurfaceIntegralUpwind`](@ref) with a given `splitting` is equivalent to the [`SurfaceIntegralStrongForm`](@ref) with `FluxUpwind(splitting)` as numerical flux (up to floating point differences). Note, that [`SurfaceIntegralUpwind`](@ref) is only available on [`TreeMesh`](@ref).

!!! warning "Experimental implementation (upwind SBP)"
    This is an experimental feature and may change in future releases.

