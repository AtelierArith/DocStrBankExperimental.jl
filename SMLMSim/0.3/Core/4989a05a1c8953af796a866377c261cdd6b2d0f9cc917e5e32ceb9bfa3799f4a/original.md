```
Line2D <: Pattern2D
```

Points with uniform random distribution between two endpoints.

# Fields

  * `λ::Float64`: Linear molecule density (molecules per micron)
  * `endpoints::Vector{Tuple{Float64,Float64}}`: Vector of endpoint coordinates
  * `n::Int`: Number of molecules in the pattern
  * `x::Vector{Float64}`: X positions of molecules in microns
  * `y::Vector{Float64}`: Y positions of molecules in microns

# Examples

```julia
# Create a line with default parameters
line = Line2D()

# Create a custom line
line = Line2D(; λ=5.0, endpoints=[(-2.0, 0.0), (2.0, 0.0)])
```
