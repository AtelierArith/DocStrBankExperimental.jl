```
load_bz(bz::AbstractBZ, [T::Type=Float64])
load_bz(bz::AbstractBZ, A::AbstractMatrix, [B::AbstractMatrix])
```

Interface to loading Brillouin zones.

## Arguments

  * `bz::AbstractBZ`: a kind of Brillouin zone to construct, e.g. [`FBZ`](@ref) or [`IBZ`](@ref)
  * `T::Type`: a numeric type to set the precision of the domain (default: `Float64`)
  * `A::AbstractMatrix`: a $d \times d$ matrix whose columns are the real-space lattice vectors of a $d$-dimensional crystal
  * `B::AbstractMatrix`: a $d \times d$ matrix whose columns are the reciprocal-space lattice vectors of a $d$-dimensional Brillouin zone (default: `A' \ 2πI`)

!!! note "Assumptions"
    `AutoBZCore` assumes that all calculations occur in the reciprocal lattice basis, since that is the basis in which Wannier interpolants are most efficiently described. See [`SymmetricBZ`](@ref) for details. We also assume that the integrands are cheap to evaluate, which is why we provide adaptive methods in the first place, so that return types can be determined at runtime (and mechanisms are in place for compile time as well)

