```
RaySplitter(idxs, transmission, refraction [, newangular]; affect)
```

Return a `RaySplitter` instance, used to perform raysplitting. `idxs` is a `Vector{Int}` with the indices of the obstacles that this `RaySplitter` corresponds to.

`transmission`, `refraction` and `newangular` are **functions**. Let `φ` be the angle of incidence and `ω` be the angular velocity and `pflag` the propagation flag (before transmission). The functions have the following signatures:

1. `transmission(φ, pflag, ω) -> T`, transmission probability.
2. `refraction(φ, pflag, ω) -> θ`, refraction angle. This angle is *relative* to the normal vector.
3. `newangular(ω, pflag) -> newω`, new angular velocity after transmission.

The above three functions use the **same convention**: the argument `pflag` is the one the obstacle has **before transmission**. For example, if a particle is outside an [`Antidot`](@ref) (with `pflag = true` here) and is transmitted inside the `Antidot` (`pflag` becomes `false` here), then all three functions will be given their second argument (the Boolean one) as `true`!

`affect` is a function, and denotes which obstacles of the billiard are affected when transmission occurs at obstacle `i` (for which obstacles should the field `pflag` be reversed). Defaults to `idxs = (i) -> i`, i.e. only the colliding obstacle is affected. If you want many obstacles to be affected you could write `idxs = (i) -> SVector(2,3,5)`, etc. Keep in mind that the only values of `i` that can be passed into this function are the ones that are given in the argument `idxs`!
