```
cell_densities(cell_positions::AbstractVector{T}) where {T<:Number}
```

Compute the cell densities from the cell positions. The returned vector `q` has  `length(q) = length(cell_positions) - 1`, with `q[i]` the density of the `i`th cell `(cell_positions[i], cell_positions[i+1])` given by  `1/(cell_positions[i+1] - cell_positions[i])`.

If you want estimates of the densities at each node rather than for a cell,  see [`node_densities`](@ref).
