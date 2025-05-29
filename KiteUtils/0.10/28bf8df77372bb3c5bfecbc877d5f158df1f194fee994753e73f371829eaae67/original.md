```
quat2viewer(q::QuatRotation)
quat2viewer(rot::AbstractMatrix)
quat2viewer(orient::AbstractVector)
```

Convert the quaternion q to the viewer reference frame. It can also be passed as a rotation matrix or as 4-element vector [w,i,j,k], where w is the real part and i, j, k are the imaginary parts of the quaternion.
