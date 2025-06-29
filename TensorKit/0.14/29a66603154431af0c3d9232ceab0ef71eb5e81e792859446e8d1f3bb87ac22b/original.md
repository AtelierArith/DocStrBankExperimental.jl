```
isposdef(t::AbstractTensor, (leftind, rightind)::Index2Tuple) -> ::Bool
```

Test whether a tensor `t` is positive definite as linear map from `rightind` to `leftind`.

If `leftind` and `rightind` are not specified, the current partition of left and right indices of `t` is used. In that case, less memory is allocated if one allows the data in `t` to be destroyed/overwritten, by using `isposdef!(t)`. Note that the permuted tensor on which `isposdef!` is called should have equal domain and codomain, as otherwise it is meaningless.
