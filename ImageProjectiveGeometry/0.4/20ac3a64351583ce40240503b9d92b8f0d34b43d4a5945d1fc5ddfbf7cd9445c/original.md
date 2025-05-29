matrix2angleaxis - Homogeneous matrix to angle-axis description

```
Usage: t = matrix2angleaxis(T)

Argument:   T - 4x4 Homogeneous transformation matrix, or 3x3 rotation matrix.
Returns:    t - 3x1 column vector giving rotation axis with magnitude equal
                to the rotation angle in radians.
```

Note that only the top left 3x3 rotation component of T is used, any translation component in T is ignored.

See also: angleaxis2matrix(),  angleaxisrotate(), angleaxis(), normaliseangleaxis()
