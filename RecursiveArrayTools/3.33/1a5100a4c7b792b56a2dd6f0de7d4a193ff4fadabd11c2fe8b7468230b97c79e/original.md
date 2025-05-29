```julia
recursive_unitless_eltype(a)
```

Grabs the unitless element type. For example, if ones has a `Array{Array{Float64,N},N}`, this will return `Array{Float64,N}`.
