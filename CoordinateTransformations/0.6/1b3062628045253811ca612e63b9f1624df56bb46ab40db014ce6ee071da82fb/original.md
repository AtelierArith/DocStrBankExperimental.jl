```
kabsch(from_points => to_points, w=ones(npoints); scale::Bool=false, svd=LinearAlgebra.svd) → trans
```

Compute the rigid transformation (or similarity transformation, if `scale=true`) that aligns `from_points` to `to_points` in a least-squares sense.

Optionally specify the non-negative weights `w` for each point. The default value of the weight is 1 for each point.

For differentiability, use `svd = GenericLinearAlgebra.svd` or other differentiable singular value decomposition.
