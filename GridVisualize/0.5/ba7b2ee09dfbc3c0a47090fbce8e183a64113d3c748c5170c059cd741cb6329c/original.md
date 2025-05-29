```julia
scalarplot(
    grid::ExtendableGrids.ExtendableGrid,
    func;
    Plotter,
    kwargs...
) -> Any

```

Plot node vector on grid as P1 FEM function on the triangulation.

If instead of the node vector,  a function is given, it will be evaluated on the grid.

If instead of the grid,  vectors for coordinates are given, a grid is created automatically.

For keyword arguments, see [`available_kwargs`](@ref)
