```julia
bedgemask!(
    grid::ExtendableGrids.ExtendableGrid,
    xa,
    xb,
    ireg::Int64;
    tol
) -> ExtendableGrids.ExtendableGrid

```

Edit region numbers of grid  boundary edges via line mask. This only works for 3D grids.
