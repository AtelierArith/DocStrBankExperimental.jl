```
qr_compact(A; kwargs...) -> Q, R
qr_compact(A, alg::AbstractAlgorithm) -> Q, R
qr_compact!(A, [QR]; kwargs...) -> Q, R
qr_compact!(A, [QR], alg::AbstractAlgorithm) -> Q, R
```

Compute the compact QR decomposition of the rectangular matrix `A` of size `(m,n)`, such that `A = Q * R` where the isometric matrix `Q` of size `(m, min(m,n))` has orthogonal columns spanning the image of `A`, and the matrix `R` of size `(min(m,n), n)` is upper triangular.

!!! note
    The bang method `qr_compact!` optionally accepts the output structure and possibly destroys the input matrix `A`. Always use the return value of the function as it may not always be possible to use the provided `QR` as output.


!!! note
    The compact QR decomposition is equivalent to the full QR decomposition when `m >= n`. Some algorithms may require `m >= n`.


See also [`qr_full(!)`](@ref qr_full).
