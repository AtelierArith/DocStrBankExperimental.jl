```julia
RGB_refine(
    source_grid::ExtendableGrids.ExtendableGrid{T, K},
    facemarkers::Vector{Bool};
    store_parents
) -> ExtendableGrids.ExtendableGrid

```

generates a new ExtendableGrid by red-green-blue mesh refinement of triangular meshes, see e.g.

Carstensen, C. –An Adaptive Mesh-Refining Algorithm Allowing for an H^1 Stable L^2 Projection onto Courant Finite Element Spaces– Constr Approx 20, 549–564 (2004). https://doi.org/10.1007/s00365-003-0550-5

The bool array facemarkers determines which faces should be bisected. Note, that a closuring is performed such that the first face in every triangle with a marked face is also refined.
