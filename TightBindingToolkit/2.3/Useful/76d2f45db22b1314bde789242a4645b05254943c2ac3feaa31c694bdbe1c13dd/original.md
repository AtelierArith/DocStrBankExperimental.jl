```julia
Meshgrid(grid::Vector{Int64} ; starts::Vector{Int64} = zeros(Int64, length(grid)))
```

returns a meshgrid of (i*1, i*2, ..., i*n) such that i*j ∈ [starts[j], starts[j] + 1, ..., grid[j]] ∀ j in [1, 2, ..., n = length(grid)]
