```
to_rotation_matrix(q)
```

Convert quaternion to 3x3 rotation matrix.

Assuming the quaternion `R` rotates a vector `v` according to

```
v' = R * v * R⁻¹,
```

we can also express this rotation in terms of a 3x3 matrix `ℛ` such that

```
v' = ℛ * v.
```

This function returns that matrix.
