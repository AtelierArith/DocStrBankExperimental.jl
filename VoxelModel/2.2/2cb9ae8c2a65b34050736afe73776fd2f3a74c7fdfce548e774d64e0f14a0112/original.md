```
reset_dl(dl::Vector{<:Real})

Updates the grid spacing to the specified vector `dl`.
!! Since the gird space is changed, the voxel space will be reseted accordingly. 
Use this function before adding geomtries to the voxel space.

# Arguments
- `dl::Vector{<:Real}`: A vector containing the new grid spacing values.
```
