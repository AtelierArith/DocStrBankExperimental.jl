```
CustomDirections{N, VN<:AbstractVector{N}} <: AbstractDirections{N, VN}
```

User-defined direction vectors.

### Fields

  * `directions`          – list of direction vectors
  * `n`                   – (optional; default: computed from `directions`)                          dimension
  * `check_boundedness`   – (optional; default: `true`) flag to check boundedness
  * `check_normalization` – (optional; default: `true`) flag to check whether all                          directions are normalized

### Notes

This struct is a wrapper for a list of user-defined directions. There are fields for the list of directions, their dimension, and (boolean) cache fields for the boundedness and normalization properties. The latter are checked by default upon construction.

To check boundedness, we construct the polyhedron with constraints $d·x <= 1$ for each direction $d$ and check if this set is bounded. (Note that the bound $1$ is arbitrary and that this set may be empty, which however implies boundedness.)

The dimension will also be determined automatically, unless the empty vector is passed (in which case the optional argument `n` needs to be specified).

### Examples

Create a template with box directions in dimension two:

```jldoctest
julia> dirs = CustomDirections([[1.0, 0.0], [-1.0, 0.0], [0.0, 1.0], [0.0, -1.0]]);

julia> dirs.directions
4-element Vector{Vector{Float64}}:
 [1.0, 0.0]
 [-1.0, 0.0]
 [0.0, 1.0]
 [0.0, -1.0]

julia> LazySets.Approximations.isbounding(dirs)
true

julia> LazySets.Approximations.isnormalized(dirs)
true
```
