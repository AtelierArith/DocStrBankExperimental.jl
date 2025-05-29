```
rightorth(t::AbstractTensorMap, (leftind, rightind)::Index2Tuple;
            alg::OrthogonalFactorizationAlgorithm = LQpos()) -> L, Q
```

Create orthonormal basis `Q` for indices in `rightind`, and remainder `L` such that `permute(t, (leftind, rightind)) = L*Q`.

If `leftind` and `rightind` are not specified, the current partition of left and right indices of `t` is used. In that case, less memory is allocated if one allows the data in `t` to be destroyed/overwritten, by using `rightorth!(t, alg = LQpos())`.

Different algorithms are available, namely `LQ()`, `LQpos()`, `RQ()`, `RQpos()`, `SVD()` and `Polar()`. `LQ()` and `LQpos()` produce a lower triangular matrix `L` and are computed using a QR decomposition of the transpose. `RQ()` and `RQpos()` produce an upper triangular remainder `L` and only works if the total left dimension is smaller than or equal to the total right dimension. `LQpos()` and `RQpos()` add an additional correction such that the diagonal elements of `L` are positive. `Polar()` produces a Hermitian and positive semidefinite `L`. Only `LQpos()`, `RQpos()` and `Polar()` are unique (no residual freedom) so that they always return the same result for the same input tensor `t`.

Orthogonality requires `InnerProductStyle(t) <: HasInnerProduct`, and `rightorth(!)` is currently only implemented for  `InnerProductStyle(t) === EuclideanInnerProduct()`.
