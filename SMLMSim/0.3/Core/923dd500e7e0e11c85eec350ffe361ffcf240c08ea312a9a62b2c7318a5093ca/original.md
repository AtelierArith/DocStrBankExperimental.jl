```
Nmer2D <: Pattern2D
```

N molecules symmetrically organized around a circle with diameter d.

# Fields

  * `n::Int`: Number of molecules in the pattern
  * `d::Float64`: Diameter of the circle in microns
  * `x::Vector{Float64}`: X positions of molecules in microns
  * `y::Vector{Float64}`: Y positions of molecules in microns

# Examples

```julia
# Create an 8-molecule pattern with 100nm diameter
nmer = Nmer2D()

# Create a custom pattern with 6 molecules and 200nm diameter
nmer = Nmer2D(; n=6, d=0.2)
```
