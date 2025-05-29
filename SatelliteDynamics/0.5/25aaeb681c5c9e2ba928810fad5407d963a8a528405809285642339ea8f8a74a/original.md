Rotation matrix, for a rotation about the x-axis.

Arguments:

  * `angle::Real`: Counter-clockwise angle of rotation as viewed looking back along the postive direction of the rotation axis.
  * `use_degrees:Bool`: If `true` interpret input as being in degrees.

Returns:

  * `r::AbstractArray{<:Real, 2}`: Rotation matrix

References:

1. O. Montenbruck, and E. Gill, *Satellite Orbits: Models, Methods and Applications*, 2012, p.27.
