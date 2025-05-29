```
Line3D <: Pattern3D
```

Points with uniform random distribution between two 3D endpoints.

# Fields

  * `λ::Float64`: Linear molecule density (molecules per micron)
  * `endpoints::Vector{Tuple{Float64,Float64,Float64}}`: Vector of 3D endpoint coordinates
  * `n::Int`: Number of molecules in the pattern
  * `x::Vector{Float64}`: X positions of molecules in microns
  * `y::Vector{Float64}`: Y positions of molecules in microns
  * `z::Vector{Float64}`: Z positions of molecules in microns

# Examples

```julia
# Create a line with default parameters
line = Line3D()

# Create a custom 3D line
line = Line3D(; λ=5.0, endpoints=[(-1.0, 0.0, -0.5), (1.0, 0.0, 0.5)])
```
