```
voxel_id = xf_to_id(n_pts, xf)
```

Returns the indices of the voxel in which it falls when a unit cube is partitioned into a regular grid of `n_pts[1]` by `n_pts[2]` by `n_pts[3]` voxels. Periodic boundary conditions are applied.

# Arguments

  * `n_pts::Tuple{Int, Int, Int}`: The number of points for each axis in the `Grid`
  * `xf::Array{Float64, 1}`: The fractional coordinates to be converted to an id

# Returns

  * `id::Array{Int, 1}`: The array indices for storing this point in space
