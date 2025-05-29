```
qrotation_x(theta)
qrotation_y(theta)
qrotation_z(theta)
```

Return a `Quaternion` object representing a rotation around the $e_x$, $e_y$, or $e_z$ axis by an angle `theta` (in radians). The quaternions returned by these functions are already normalized and can be used with the function `rotationmatrix_normalized`.
