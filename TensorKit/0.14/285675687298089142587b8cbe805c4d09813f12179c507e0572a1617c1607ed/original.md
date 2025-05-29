```
eigh(t::AbstractTensorMap, (leftind, rightind)::Index2Tuple) -> D, V
```

Compute eigenvalue factorization of tensor `t` as linear map from `rightind` to `leftind`. The function `eigh` assumes that the linear map is hermitian and `D` and `V` tensors with the same `scalartype` as `t`. See `eig` and `eigen` for non-hermitian tensors. Hermiticity requires that the tensor acts on inner product spaces, and the current implementation requires `InnerProductStyle(t) === EuclideanInnerProduct()`.

If `leftind` and `rightind` are not specified, the current partition of left and right indices of `t` is used. In that case, less memory is allocated if one allows the data in `t` to be destroyed/overwritten, by using `eigh!(t)`. Note that the permuted tensor on which `eigh!` is called should have equal domain and codomain, as otherwise the eigenvalue decomposition is meaningless and cannot satisfy

```
permute(t, (leftind, rightind)) * V = V * D
```

See also `eigen` and `eig`.
