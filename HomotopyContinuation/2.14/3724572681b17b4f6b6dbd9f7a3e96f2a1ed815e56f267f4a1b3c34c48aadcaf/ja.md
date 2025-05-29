```
linear_subspace_homotopy(F, V::LinearSubspace, W::LinearSubspace, intrinsic = nothing)
```

[`IntrinsicSubspaceHomotopy`](@ref)（`dim(V) < codim(V)` または `intrinsic = true` の場合）または [`ExtrinsicSubspaceHomotopy`](@ref) を構築します。直接のコンストラクタと比較して、これは同次系も考慮します。
