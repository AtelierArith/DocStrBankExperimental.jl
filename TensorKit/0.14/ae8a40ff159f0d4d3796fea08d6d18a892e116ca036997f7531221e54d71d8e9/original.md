```
eig(t::AbstractTensor, (leftind, rightind)::Index2Tuple; kwargs...) -> D, V
```

Compute eigenvalue factorization of tensor `t` as linear map from `rightind` to `leftind`. The function `eig` assumes that the linear map is not hermitian and returns type stable complex valued `D` and `V` tensors for both real and complex valued `t`. See `eigh` for hermitian linear maps

If `leftind` and `rightind` are not specified, the current partition of left and right indices of `t` is used. In that case, less memory is allocated if one allows the data in `t` to be destroyed/overwritten, by using `eig!(t)`. Note that the permuted tensor on which `eig!` is called should have equal domain and codomain, as otherwise the eigenvalue decomposition is meaningless and cannot satisfy

```
permute(t, (leftind, rightind)) * V = V * D
```

Accepts the same keyword arguments `scale` and `permute` as `eigen` of dense matrices. See the corresponding documentation for more information.

See also `eigen` and `eigh`.
