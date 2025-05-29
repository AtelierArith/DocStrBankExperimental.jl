```
MomentumAdvection(; dealiasing = :quadratic)
```

Advective transport of momentum ($u_i$, i.e. normalized by density) in rotation form. Only the velocity–vorticity products are computed, while the gradient of kinetic energy is assumed to be handled as part of a modified pressure term.

# Keywords

  * `dealiasing`: The level of dealiasing, determining the physical-domain resolution at which multiplications are performed. The default `:quadratic` setting relies on the “3/2-rule” to avoid aliasing errors for the products that are computed as part of the momentum advection term. Alternatively, `dealiasing` can be set to `nothing` for a physical-domain resolution that matches the frequency-domain resolution (rounded up to an even value), or to a tuple of two integers to set the resolution manually.
