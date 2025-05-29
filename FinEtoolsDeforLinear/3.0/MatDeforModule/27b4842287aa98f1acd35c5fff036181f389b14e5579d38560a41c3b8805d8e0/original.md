```
rotstressvec!(::Type{DeforModelRed3D},  outstress::Vector{T},  instress::Vector{T}, Rm::_RotationMatrix) where {T}
```

Rotate the stress vector by the supplied rotation matrix.

Calculate the rotation of the stress vector to the 'bar' coordinate system given by the columns of the rotation matrix `Rm`.

  * `outstress` = output stress vector, overwritten inside
  * `instress` = input stress vector
  * `Rm` = columns are components of 'bar' basis vectors on the 'plain'    basis vectors
