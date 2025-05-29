```julia
recursive_unitless_bottom_eltype(a)
```

Grabs the unitless element type at the bottom of the chain. For example, if ones has a `Array{Array{Float64,N},N}`, this will return `Float64`.
