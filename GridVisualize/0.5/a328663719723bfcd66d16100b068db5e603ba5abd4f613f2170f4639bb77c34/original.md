```julia
gridplot!(
    ctx::Union{Nothing, Dict{Symbol, Any}},
    grid::ExtendableGrids.ExtendableGrid;
    kwargs...
)

```

Plot grid into subplot in the visualizer. If `[i,j]` is omitted, `[1,1]` is assumed.

Keyword arguments: see [`available_kwargs`](@ref)
