```
log(::LieGroup{ℝ, AbelianMultiplicationGroupOperation, Sphere}, g)
log!(::LieGroup{ℝ, AbelianMultiplicationGroupOperation, Sphere}, X, g)
```

Compute the Lie group logarithm on the [`CircleGroup`](@ref), represented as two dimensional vectors in the real plane. It coincides with the ordinary complex logarithm after canonical identification of the real plane with the complex plane.

This can be computed in-place of `X`.
