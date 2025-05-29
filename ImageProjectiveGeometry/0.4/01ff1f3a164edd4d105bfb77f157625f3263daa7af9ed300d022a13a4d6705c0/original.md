angleaxis2matrix - Converts angle-axis descriptor to 4x4 homogeneous transformation  matrix

```
Usage:     T = angleaxis2matrix(t)

Argument:  t - 3x1 vector specifying the rotation axis and having 
               magnitude equal to the rotation angle in radians.
Returns:   T - 4x4 Homogeneous transformation matrix.
```

See also: matrix2angleaxis(), angleaxisrotate(), angleaxis(), normaliseangleaxis()
