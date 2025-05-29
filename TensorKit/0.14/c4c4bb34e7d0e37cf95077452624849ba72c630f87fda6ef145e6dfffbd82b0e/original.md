```
leftorth(t::AbstractTensorMap, (leftind, rightind)::Index2Tuple;
            alg::OrthogonalFactorizationAlgorithm = QRpos()) -> Q, R
```

Create orthonormal basis `Q` for indices in `leftind`, and remainder `R` such that `permute(t, (leftind, rightind)) = Q*R`.

If `leftind` and `rightind` are not specified, the current partition of left and right indices of `t` is used. In that case, less memory is allocated if one allows the data in `t` to be destroyed/overwritten, by using `leftorth!(t, alg = QRpos())`.

Different algorithms are available, namely `QR()`, `QRpos()`, `SVD()` and `Polar()`. `QR()` and `QRpos()` use a standard QR decomposition, producing an upper triangular matrix `R`. `Polar()` produces a Hermitian and positive semidefinite `R`. `QRpos()` corrects the standard QR decomposition such that the diagonal elements of `R` are positive. Only `QRpos()` and `Polar()` are unique (no residual freedom) so that they always return the same result for the same input tensor `t`.

Orthogonality requires `InnerProductStyle(t) <: HasInnerProduct`, and `leftorth(!)` is currently only implemented for      `InnerProductStyle(t) === EuclideanInnerProduct()`.
