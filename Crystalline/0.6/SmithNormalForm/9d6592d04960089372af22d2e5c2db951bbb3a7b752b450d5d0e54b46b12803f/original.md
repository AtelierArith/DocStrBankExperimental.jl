```
smith(X::AbstractMatrix{P}; inverse::Bool=true) --> Smith{P,Q,V}
```

Return a Smith normal form of an integer matrix `X` as a `Smith` structure (of element type `P`, matrix type `Q`, and invariant factor type `V`).

The Smith normal form is well-defined for any matrix $m×n$ matrix `X` with elements in a principal domain (PID; e.g., integers) and provides a decomposition of `X` into $m×m$, $m×n$, and `S`, `Λ`, and `T` as `X = SΛT`, where `Λ` is a diagonal matrix with entries  ("invariant factors") Λᵢ ≥ Λᵢ₊₁ ≥ 0 with nonzero entries divisible in the sense Λᵢ | Λᵢ₊₁. The invariant factors can be obtained from [`diag(::Smith)`](@ref).

`S` and `T` are invertible matrices; if the keyword argument `inverse` is true (default), the inverse matrices are computed and returned as part of the `Smith` factorization.
