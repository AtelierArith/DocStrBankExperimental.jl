```
dihedral(v1, v2, v3, v4; degrees=true)
dihedral(v::AbstractVector; degrees=true)
```

Computes the dihedral angle between the planes formed by the vectors `v1-v2` and `v2-v3`, and `v2-v3` and `v3-v4`. The input vectors must have 3 elements. The function returns the dihedral angle in radians or degrees. If the input is a vector with 4 vectors, the function computes the dihedral angle between the planes  formed by the vectors `v[1]-v[2]` and `v[2]-v[3]`, and `v[2]-v[3]` and `v[3]-v[4]`.

The optional argument `degrees` specifies whether the output is in degrees (default) or radians.
