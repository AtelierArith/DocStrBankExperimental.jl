```julia
struct NamedTuple{(:lower, :upper), Tuple{Vector{Float64}, Vector{Float64}}}
```

The bounds of the region. Consists of the lower and upper bounds, each a list of floating-point values.
