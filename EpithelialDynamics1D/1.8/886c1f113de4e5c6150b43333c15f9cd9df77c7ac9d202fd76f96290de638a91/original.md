```
cell_midpoints(cell_positions::AbstractVector{T}) where {T<:Number}
```

Compute the midpoints of the cells from the cell positions. The returned vector `x` has `length(x) = length(cell_positions) - 1`, with `x[i]` the midpoint of the `i`th cell `(cell_positions[i], cell_positions[i+1])` given by  `0.5(cell_positions[i] + cell_positions[i+1])`.
