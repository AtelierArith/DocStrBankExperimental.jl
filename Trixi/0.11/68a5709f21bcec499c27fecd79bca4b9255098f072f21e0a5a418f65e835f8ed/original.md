```
splitting_lax_friedrichs(u, orientation::Integer,
                         equations::LinearScalarAdvectionEquation1D)
splitting_lax_friedrichs(u, which::Union{Val{:minus}, Val{:plus}}
                         orientation::Integer,
                         equations::LinearScalarAdvectionEquation1D)
```

Naive local Lax-Friedrichs style flux splitting of the form `f⁺ = 0.5 (f + λ u)` and `f⁻ = 0.5 (f - λ u)` where `λ` is the absolute value of the advection velocity.

Returns a tuple of the fluxes "minus" (associated with waves going into the negative axis direction) and "plus" (associated with waves going into the positive axis direction). If only one of the fluxes is required, use the function signature with argument `which` set to `Val{:minus}()` or `Val{:plus}()`.

!!! warning "Experimental implementation (upwind SBP)"
    This is an experimental feature and may change in future releases.

