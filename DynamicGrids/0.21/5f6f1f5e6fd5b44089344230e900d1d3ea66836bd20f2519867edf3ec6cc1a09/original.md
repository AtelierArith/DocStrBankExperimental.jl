```
SetGridRule <: Rule
```

A `Rule` applies to whole grids. This is used for operations that don't benefit from having neighborhood buffering or looping over the grid handled for them, or any specific optimisations. Best suited to simple functions like `rand!(grid)` or using convolutions from other packages like DSP.jl. They may also be useful for doing other custom things that don't fit into the DynamicGrids.jl framework during the simulation.

Grid rules specify the grids they want and are sequenced just like any other grid.

```julia
struct MySetGridRule{R,W} <: SetGridRule{R,W} end
```

And applied as:

```julia
function applyrule!(data::AbstractSimData, rule::MySetGridRule{R,W}) where {R,W}
    rand!(data[W])
end
```
