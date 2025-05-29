A Cell represents a periodic structure in three-dimensional space.

Defined as:

```julia
mutable struct Cell{T}
    lattice::Lattice{T}                 # Lattice of the structure
    symbols::Vector{Symbol}
    positions::Matrix{T}
    arrays::Dict{Symbol, Any}        # Any additional arrays
    metadata::Dict{Symbol, Any}
end
```
