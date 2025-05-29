```
make_coordinates(x::T, y::T, z::T) where {T<:AbstractArray{<:Real}}
```

Create a 3D meshgrid of Coordinates from arrays `x`, `y`, and `z` and return it as a StructArray.

# Arguments

  * `x::T`: Array of x-coordinates per voxel.
  * `y::T`: Array of y-coordinates per voxel.
  * `z::T`: Array of z-coordinates per voxel.
