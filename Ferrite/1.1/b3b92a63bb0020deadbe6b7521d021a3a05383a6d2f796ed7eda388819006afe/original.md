```
reinit!(
    iv::InterfaceValues,
    cell_here::AbstractCell, coords_here::AbstractVector{Vec{dim, T}}, facet_here::Int,
    cell_there::AbstractCell, coords_there::AbstractVector{Vec{dim, T}}, facet_there::Int
)
```

Update the [`InterfaceValues`](@ref) for the interface between `cell_here` (with cell coordinates `coords_here`) and `cell_there` (with cell coordinates `coords_there`). `facet_here` and `facet_there` are the (local) facet numbers for the respective cell.
