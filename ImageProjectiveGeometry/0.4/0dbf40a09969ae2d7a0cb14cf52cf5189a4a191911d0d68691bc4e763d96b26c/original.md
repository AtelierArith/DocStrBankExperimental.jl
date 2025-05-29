quaternionrotate - Rotates a 3D vector by a quaternion 

```
Usage:   vnew = quaternionrotate(Q, v)

Arguments: Q - a quaternion in the form [w, xi, yj, zk]
           v - a vector to rotate, either an inhomogeneous 3-vector or a
               homogeneous 4-vector.
Returns:   vnew - rotated vector.
```

See also: matrix2quaternion(), quaternion2matrix(), quaternion()
