```julia
simplexgrid(
    ::Type{SimplexGridFactory.TetGenType},
    TetGen,
    input;
    kwargs...
) -> ExtendableGrids.ExtendableGrid

```

Create Grid from TetGen data.

See [`default_options`](@ref) for available `kwargs`.
