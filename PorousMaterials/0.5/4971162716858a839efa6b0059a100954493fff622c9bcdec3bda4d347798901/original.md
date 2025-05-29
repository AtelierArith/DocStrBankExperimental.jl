```
xf = id_to_xf(voxel_id, n_pts)
```

Given a `voxel_id` in a `Grid`, return the fractional coordinates to which this voxel corresponds.

# Arguments

  * `n_pts::Tuple{Int, Int, Int}`: The number of voxels along each axis in the `Grid`
  * `voxel_id::Array{Int, 1}`: the voxel coordinates in `grid.data`

# Returns

  * `xf::Array{Float64, 1}`: The fractional coordinates corresponding to the grid voxel
