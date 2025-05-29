```julia
scalarplot!(
    ctx::Union{Nothing, Dict{Symbol, Any}},
    grids::Array{ExtendableGrids.ExtendableGrid{Tv, Ti}, 1},
    parentgrid::ExtendableGrids.ExtendableGrid{Tv, Ti},
    funcs::AbstractVector;
    kwargs...
) -> Any

```

Plot node vectors on subgrids of parent grid as P1 FEM function on the triangulation into subplot in the visualizer. If `[i,j]` is omitted, `[1,1]` is assumed. eyword arguments: see [`available_kwargs`](@ref)
