```julia
cellmask!(
    grid::ExtendableGrids.ExtendableGrid,
    maskmin,
    maskmax,
    ireg::Int64;
    tol
) -> ExtendableGrids.ExtendableGrid

```

Edit region numbers of grid cells via rectangular mask.

Examples: [Rectangle-with-multiple-regions](@ref)
