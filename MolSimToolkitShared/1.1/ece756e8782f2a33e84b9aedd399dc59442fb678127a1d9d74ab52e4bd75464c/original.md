```
center_of_mass(x::AbstractVector{<:AbstractVector}[, mass::AbstractVector=nothing])
```

Calculate the center of mass of a set of points.

# Arguments

  * `x::AbstractVector{<:AbstractVector}`: A vector of coordinates.
  * `mass::AbstractVector`: A vector of masses. If not provided, all masses are assumed to be equal.

# Example

```jldoctest
julia> import MolSimToolkitShared: center_of_mass

julia> x = [ [1.0, 2.0, 3.0], [4.0, 5.0, 6.0], [7.0, 8.0, 9.0] ];

julia> center_of_mass(x)
3-element Vector{Float64}:
 4.0
 5.0
 6.0

julia> center_of_mass(x, [1.0, 2.0, 3.0]) # providing masses
3-element Vector{Float64}:
 5.0
 6.0
 7.0

```
