```
left_polar(A; kwargs...) -> W, P
left_polar(A, alg::AbstractAlgorithm) -> W, P
left_polar!(A, [WP]; kwargs...) -> W, P
left_polar!(A, [WP], alg::AbstractAlgorithm) -> W, P
```

Compute the full polar decomposition of the rectangular matrix `A` of size `(m, n)` with `m >= n`, such that `A = W * P`. Here, `W` is an isometric matrix (orthonormal columns) of size `(m, n)`, whereas `P` is a positive (semi)definite matrix of size `(n, n)`.

!!! note
    The bang method `left_polar!` optionally accepts the output structure and possibly destroys the input matrix `A`. Always use the return value of the function as it may not always be possible to use the provided `WP` as output.


See also [`right_polar(!)`](@ref right_polar).
