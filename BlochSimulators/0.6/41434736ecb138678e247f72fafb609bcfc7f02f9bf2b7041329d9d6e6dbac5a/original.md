```
Coordinates{T<:Real}
```

Basic type that holds the spatial coordinates of a voxel. Note that when performing signal simulations, `StructArray{<:Coordinates}`s are used to store the coordinates of all voxels. Such arrays are created using the `make_coordinates`.

# Fields

  * `x::T`: Position of voxel along the x direction
  * `y::T`: Position of voxel along the y direction
  * `z::T`: Position of voxel along the z direction (not used for 2D simulations)
