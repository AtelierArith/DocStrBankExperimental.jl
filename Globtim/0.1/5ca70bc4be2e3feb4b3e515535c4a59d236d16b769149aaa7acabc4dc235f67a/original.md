```
struct test_input
```

A structure containing all parameters needed to run a test.

# Fields

  * `dim::Int`: Dimension of the problem space
  * `center::Vector{Float64}`: Center point of the sampling region
  * `GN::Union{Int, Nothing}`: Number of samples (optional)
  * `prec::Union{Tuple{Float64,Float64}, Nothing}`: Precision parameters (α, δ)
  * `tolerance::Union{Float64, Nothing}`: Convergence tolerance
  * `noise::Union{Tuple{Float64,Float64}, Nothing}`: Noise parameters
  * `sample_range::Union{Float64, Nothing}`: Range for sampling around center
  * `reduce_samples::Union{Float64, Nothing}`: Reduction factor for sample set size
  * `objective::Function`: Objective function to be evaluated

# Constructor

```
test_input(f::Function; kwargs...)
```

# Keyword Arguments

  * `dim::Int=2`: Problem dimension
  * `center::AbstractVector{Float64}=fill(0.0, dim)`: Center point
  * `alpha::Float64=0.1`: First precision parameter
  * `delta::Float64=0.5`: Second precision parameter
  * `tolerance::Float64=2e-3`: Convergence tolerance
  * `sample_range::Number=1.0`: Sampling range around center
  * `reduce_samples::Float64=1.0`: Sample reduction factor
  * `model=nothing`: Optional model parameter passed to objective function
  * `outputs=nothing`: Optional outputs parameter passed to objective function
