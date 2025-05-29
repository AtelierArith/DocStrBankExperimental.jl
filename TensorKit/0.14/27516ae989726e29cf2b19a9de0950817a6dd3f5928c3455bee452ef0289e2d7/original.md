```
rightnull(t::AbstractTensor, (leftind, rightind)::Index2Tuple;
            alg::OrthogonalFactorizationAlgorithm = LQ(),
            atol::Real = 0.0,
            rtol::Real = eps(real(float(one(scalartype(t)))))*iszero(atol)) -> N
```

Create orthonormal basis for the orthogonal complement of the support of the indices in `rightind`, such that `permute(t, (leftind, rightind))*N' = 0`.

If `leftind` and `rightind` are not specified, the current partition of left and right indices of `t` is used. In that case, less memory is allocated if one allows the data in `t` to be destroyed/overwritten, by using `rightnull!(t, alg = LQpos())`.

Different algorithms are available, namely `LQ()` (or equivalently, `LQpos`), `SVD()` and `SDD()`. The first assumes that the matrix is full rank and requires `iszero(atol)` and `iszero(rtol)`. With `SVD()` and `SDD()`, `rightnull` will use the corresponding singular value decomposition, and one can specify an absolute or relative tolerance for which singular values are to be considered zero, where `max(atol, norm(t)*rtol)` is used as upper bound.

Orthogonality requires `InnerProductStyle(t) <: HasInnerProduct`, and `rightnull(!)` is currently only implemented for  `InnerProductStyle(t) === EuclideanInnerProduct()`.
