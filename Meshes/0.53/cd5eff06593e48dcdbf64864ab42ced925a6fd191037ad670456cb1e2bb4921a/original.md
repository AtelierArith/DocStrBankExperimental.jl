```
Affine(A, b)
```

Affine transform `Ax + b` with matrix `A` and vector `b`.

# Examples

```julia
Affine(AngleAxis(0.2, 1.0, 0.0, 0.0), [-2, 2, 2])
Affine(Angle2d(π / 2), SVector(2, -2))
Affine([0 -1; 1 0], [-2, 2])
```
