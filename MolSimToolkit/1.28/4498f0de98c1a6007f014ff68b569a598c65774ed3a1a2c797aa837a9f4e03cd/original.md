```
UnitCell{T}
```

A structure to store the unit cell of a frame in the trajectory. The unit cell is represented by a 3x3 matrix of type `SMatrix{3,3,T,9}`.

The `valid` field indicates if the unit cell is valid (not zero). The `orthorhombic` field indicates if the unit cell is orthorhombic (all angles are 90 degrees).
