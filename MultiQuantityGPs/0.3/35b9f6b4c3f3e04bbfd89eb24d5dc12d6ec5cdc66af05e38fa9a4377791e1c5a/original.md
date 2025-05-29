```julia
struct NamedTuple{(:x, :y), Tuple{Tuple{Vector{Float64}, Int64}, Float64}}
```

Type of sample measurement with noise, the measurement mean and standard deviation
