```
right_polar(A; kwargs...) -> P, Wᴴ
right_polar(A, alg::AbstractAlgorithm) -> P, Wᴴ
right_polar!(A, [PWᴴ]; kwargs...) -> P, Wᴴ
right_polar!(A, [PWᴴ], alg::AbstractAlgorithm) -> P, Wᴴ
```

Compute the full polar decomposition of the rectangular matrix `A` of size `(m, n)` with `n >= m`, such that `A = P * Wᴴ`. Here, `P` is a positive (semi)definite matrix of size `(m, m)`, whereas `Wᴴ` is a matrix with orthonormal rows (its adjoint is isometric) of size `(n, m)`.

!!! note
    The bang method `right_polar!` optionally accepts the output structure and possibly destroys the input matrix `A`. Always use the return value of the function as it may not always be possible to use the provided `WP` as output.


See also [`left_polar(!)`](@ref left_polar).
