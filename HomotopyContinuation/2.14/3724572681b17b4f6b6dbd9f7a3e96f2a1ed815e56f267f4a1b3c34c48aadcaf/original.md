```
linear_subspace_homotopy(F, V::LinearSubspace, W::LinearSubspace, intrinsic = nothing)
```

Constructs an [`IntrinsicSubspaceHomotopy`](@ref) (if `dim(V) < codim(V)` or `intrinsic = true`) or [`ExtrinsicSubspaceHomotopy`](@ref). Compared to the direct constructor, this also takes care of homogeneous systems.
