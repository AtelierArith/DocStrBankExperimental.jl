```
CSys(sdim::IT1, mdim::IT2, z::T, computecsmat::F) where {IT1, IT2, T <: Number, F <: Function}
```

Construct coordinate system when the function to compute the rotation matrix of type `T` is given.

  * `z` = zero value,
  * The `computecsmat` function signature:   `update!(           csmatout::AbstractMatrix{<:Real},           XYZ::AbstractVecOrMat{<:Real},           tangents::AbstractMatrix{<:Real},           feid::Integer,           qpid::Integer,       )`   where

      * `csmatout`= output matrix buffer, of size `(sdim, mdim)`;
      * `XYZ`= location  in physical coordinates;
      * `tangents`= tangent vector matrix, tangents to the parametric coordinate curves  in the element;
      * `feid`= finite element identifier;
      * `qpid`= quadrature point identifier.

# Example

```
# Cylindrical coordinate system: NO ALLOCATIONS WHATSOEVER!
@views function compute!(csmatout, XYZ, tangents, feid, qpid)
    center = (0.0, 0.0, 0.0)
    xyz = (XYZ[1], XYZ[2], XYZ[3])
    csmatout[:, 1] .= xyz .- center
    csmatout[3, 1] = 0.0
    csmatout[:, 1] ./= norm(csmatout[:, 1])
    csmatout[:, 3] .= (0.0, 0.0, 1.0)
    cross3!(csmatout[:, 2], csmatout[:, 3], csmatout[:, 1])
    csmatout[:, 2] ./=  norm(csmatout[:, 2])
    return csmatout
end
```
