```
leftnull(t::AbstractTensor, (leftind, rightind)::Index2Tuple;
            alg::OrthogonalFactorizationAlgorithm = QRpos()) -> N
```

Create orthonormal basis for the orthogonal complement of the support of the indices in `leftind`, such that `N' * permute(t, (leftind, rightind)) = 0`.

If `leftind` and `rightind` are not specified, the current partition of left and right indices of `t` is used. In that case, less memory is allocated if one allows the data in `t` to be destroyed/overwritten, by using `leftnull!(t, alg = QRpos())`.

Different algorithms are available, namely `QR()` (or equivalently, `QRpos()`), `SVD()` and `SDD()`. The first assumes that the matrix is full rank and requires `iszero(atol)` and `iszero(rtol)`. With `SVD()` and `SDD()`, `rightnull` will use the corresponding singular value decomposition, and one can specify an absolute or relative tolerance for which singular values are to be considered zero, where `max(atol, norm(t)*rtol)` is used as upper bound.

Orthogonality requires `InnerProductStyle(t) <: HasInnerProduct`, and `leftnull(!)` is currently only implemented for  `InnerProductStyle(t) === EuclideanInnerProduct()`.
