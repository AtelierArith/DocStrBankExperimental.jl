```
Integrator{T<:AbstractFloat}
```

Integrator. Used as a functor to integrate a [`State`](@ref).

# Fields

  * `scheme::Function` : The integration scheme to use.
  * `h::T` : Step size.
  * `t0::T` : Initial time.
  * `tmax::T` : Duration of simulation.
