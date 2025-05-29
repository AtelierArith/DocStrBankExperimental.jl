```
quat2euler(q::QuatRotation)
quat2euler(q::AbstractVector)
```

Convert a quaternion to roll, pitch, and yaw angles in radian. The quaternion can be a 4-element vector (w, i, j, k) or a QuatRotation object.
