```julia
filling2isoval(
    flat::Crystalline.AbstractFourierLattice{D}
) -> Any
filling2isoval(
    flat::Crystalline.AbstractFourierLattice{D},
    filling::Real
) -> Any
filling2isoval(
    flat::Crystalline.AbstractFourierLattice{D},
    filling::Real,
    nsamples::Integer
) -> Any

```

Return the isovalue of `flat` such that the interior of the thusly defined levelset isosurface encloses a fraction `filling` of the unit cell.

The keyword argument `nsamples` specifies the grid-resolution used in evaluating this answer (via Statistics.jl's `quantile`).
