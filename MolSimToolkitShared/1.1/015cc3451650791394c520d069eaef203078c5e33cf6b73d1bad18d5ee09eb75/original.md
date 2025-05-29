```
wrap_to_first(x, unit_cell_matrix)
```

Wraps the coordinates of point `x` such that the returning coordinates are in the first unit cell with all-positive coordinates. The unit cell  has to be a matrix of size `(N,N)`.

## Example

```jldoctest
julia> using MolSimToolkitShared: wrap_to_first

julia> uc = [10.0 0.0 0.0; 0.0 10.0 0.0; 0.0 0.0 10.0]
3×3 Matrix{Float64}:
 10.0   0.0   0.0
  0.0  10.0   0.0
  0.0   0.0  10.0

julia> wrap_to_first([15.0, 13.0, 2.0], uc)
3-element Vector{Float64}:
 5.0
 3.0000000000000004
 2.0
```
