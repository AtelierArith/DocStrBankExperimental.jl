```julia
mutable struct ErrorData
```

Structure to hold error values compared to analytical solutions for multiple computations. Can be used to generate plots.

# Fields

  * `p::Vector{Float64}`: PDE parameters.
  * `n::Vector{Int64}`: Number of gridpoints
  * `eps::Vector{Float64}`: Accuracy
  * `errors::Vector{Vector{Float64}}`: Errors
