```julia
isoval2filling(
    flat::Crystalline.AbstractFourierLattice{D},
    isoval::Real
) -> Any
isoval2filling(
    flat::Crystalline.AbstractFourierLattice{D},
    isoval::Real,
    nsamples::Integer
) -> Any

```

Return the filling fraction of the interior of the isosurface defined by `flat` for an isovalue `isoval`.

The keyword argument `nsamples` specifies the grid-resolution used in evaluating this answer (using staircase integration).
