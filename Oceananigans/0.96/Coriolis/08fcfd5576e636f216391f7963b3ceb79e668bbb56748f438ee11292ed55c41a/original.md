```
struct NonTraditionalBetaPlane{FT} <: AbstractRotation
```

A Coriolis implementation that accounts for the latitudinal variation of both the locally vertical and the locally horizontal components of the rotation vector. The "traditional" approximation in ocean models accounts for only the locally vertical component of the rotation vector (see [`BetaPlane`](@reface)).

This implementation is based off of section 5 of [Dellar2011](@citet) and it conserves energy, angular momentum, and potential vorticity.

# References

Dellar, P. (2011). Variations on a beta-plane: Derivation of non-traditional     beta-plane equations from Hamilton's principle on a sphere. Journal of     Fluid Mechanics, 674, 174-195. doi:10.1017/S0022112010006464
