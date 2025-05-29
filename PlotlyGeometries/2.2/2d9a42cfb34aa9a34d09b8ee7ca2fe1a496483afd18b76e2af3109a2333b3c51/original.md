```
grot!(geo::GenericTrace, rotang::Vector{<:Real}, center::Vector{<:Real}=[0])

Rotates a 3D geometry around a specified center point. (Tait–Bryan rotation)

# Arguments
- `geo::GenericTrace`: The 3D geometry to be rotated, which must have `x`, `y`, and `z` coordinates.
- `rotang::Vector{<:Real}`: A vector of three Tait–Bryan rotation angles in degrees  for rotations around the x, y, and z axes respectively.
- `center::Vector{<:Real}`: The center point of rotation. Default is `[0]`, which means the rotation center will be set at the geometric center of the object.
```
