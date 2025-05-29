```
VisualizeSols(sols::AbstractVector{<:AbstractODESolution}; OverWrite::Bool=true)
```

Visualizes vectors of type `ODESolution` using the `Plots.jl` package. If `OverWrite=false`, the solution is displayed on top of the previous plot object.
