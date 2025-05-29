```julia
scalarplot!(
    ctx::Union{Nothing, Dict{Symbol, Any}},
    grid::ExtendableGrids.ExtendableGrid,
    func;
    kwargs...
)

```

Plot node vector on grid as P1 FEM function on the triangulation into subplot in the visualizer. If `[i,j]` is omitted, `[1,1]` is assumed.

If instead of the node vector,  a function is given, it will be evaluated on the grid.

If instead of the grid, coordinate vectors are given, a temporary grid is created.

Keyword arguments: see [`available_kwargs`](@ref)
