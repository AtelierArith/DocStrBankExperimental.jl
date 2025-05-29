```
qr_full(A; kwargs...) -> Q, R
qr_full(A, alg::AbstractAlgorithm) -> Q, R
qr_full!(A, [QR]; kwargs...) -> Q, R
qr_full!(A, [QR], alg::AbstractAlgorithm) -> Q, R
```

Compute the full QR decomposition of the rectangular matrix `A`, such that `A = Q * R` where `Q` is a square unitary matrix with the same number of rows as `A` and `R` is an upper triangular matrix with the same size as `A`.

!!! note
    The bang method `qr_full!` optionally accepts the output structure and possibly destroys the input matrix `A`. Always use the return value of the function as it may not always be possible to use the provided `QR` as output.


See also [`qr_compact(!)`](@ref qr_compact).
