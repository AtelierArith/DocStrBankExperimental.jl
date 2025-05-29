```
from_rotation_matrix(ℛ)
```

Convert 3x3 rotation matrix to quaternion.

Assuming the 3x3 matrix `ℛ` rotates a vector `v` according to

```
v' = ℛ * v,
```

we can also express this rotation in terms of a quaternion `R` such that

```
v' = R * v * R⁻¹.
```

This function returns that quaternion, using Bar-Itzhack's algorithm (version 3) to allow for non-orthogonal matrices.  [J. Guidance, Vol. 23, No. 6, p. 1085](http://dx.doi.org/10.2514/2.4654)

!!! note
    If you want to use this function for matrices with elements of types other than `Float64` or `Float32`, you will need to (install and) import `GenericLinearAlgebra` first.  The reason is that this function computes the eigen-decomposition of `ℛ`, which is only available for more generic float types via that package.  Note that you will want at least version 0.3.11 of `GenericLinearAlgebra` because previous versions had a bug.

