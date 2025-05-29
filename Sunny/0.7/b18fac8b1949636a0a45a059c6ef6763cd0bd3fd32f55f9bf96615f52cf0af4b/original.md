```
lattice_vectors(a, b, c, α, β, γ)
```

Return the lattice vectors, as columns of the $3×3$ output matrix, that define the shape of a crystallographic cell in global Cartesian coordinates. Conversely, one can view the output matrix as defining the global Cartesian coordinate system with respect to the lattice system.

The lattice constants $(a, b, c)$ have units of length, and the angles $(α, β, γ)$ are in degrees. The inverse mapping is [`lattice_params`](@ref).

# Example

```julia
latvecs = lattice_vectors(1, 1, 2, 90, 90, 120)
a1, a2, a3 = eachcol(latvecs)
@assert a1 ≈ [1, 0, 0]       # a1 always aligned with global x
@assert a2 ≈ [-1/2, √3/2, 0] # a2 always in global (x,y) plane
@assert a3 ≈ [0, 0, 2]       # a3 may generally be a combination of (x,y,z)
```
