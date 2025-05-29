```
levelsetlattice(sgnum::Integer, D::Integer=2, idxmax::NTuple=ntuple(i->2,D))
    --> UnityFourierLattice{D}
```

Compute a "neutral"/uninitialized Fourier lattice basis, a [`UnityFourierLattice`](@ref), consistent with the symmetries of the space group `sgnum` in dimension `D`.  The resulting lattice `flat` is expanded in a Fourier basis split into symmetry-derived orbits, with intra-orbit coefficients constrained by the symmetries of the space-group. The inter-orbit coefficients are, however, free and unconstrained.

The Fourier resolution along each reciprocal lattice vector is controlled by `idxmax`: e.g., if `D = 2` and `idxmax = (2, 3)`, the resulting Fourier lattice may contain  reciprocal lattice vectors (k₁, k₂) with k₁∈[0,±1,±2] and k₂∈[0,±1,±2,±3], referred  to a 𝐆-basis.

This "neutral" lattice can, and usually should, be subsequently modulated by [`modulate`](@ref) (which modulates the inter-orbit coefficients, which may eliminate "synthetic symmetries" that can exist in the "neutral" configuration, due to all  inter-orbit coefficients being set to unity).

## Examples

Compute a `UnityFourierLattice`, modulate it with random inter-orbit coefficients  via `modulate`, and finally plot it (via PyPlot.jl):

```julia-repl
julia> uflat = levelsetlattice(16, Val(2))
julia> flat  = modulate(uflat)
julia> Rs    = directbasis(16, Val(2)) 
julia> using PyPlot
julia> plot(flat, Rs)
```
