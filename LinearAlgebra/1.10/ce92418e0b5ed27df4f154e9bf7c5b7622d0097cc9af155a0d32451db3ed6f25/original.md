```
lu(A, pivot = RowMaximum(); check = true) -> F::LU
```

Compute the LU factorization of `A`.

When `check = true`, an error is thrown if the decomposition fails. When `check = false`, responsibility for checking the decomposition's validity (via [`issuccess`](@ref)) lies with the user.

In most cases, if `A` is a subtype `S` of `AbstractMatrix{T}` with an element type `T` supporting `+`, `-`, `*` and `/`, the return type is `LU{T,S{T}}`.

In general, LU factorization involves a permutation of the rows of the matrix (corresponding to the `F.p` output described below), known as "pivoting" (because it corresponds to choosing which row contains the "pivot", the diagonal entry of `F.U`). One of the following pivoting strategies can be selected via the optional `pivot` argument:

  * `RowMaximum()` (default): the standard pivoting strategy; the pivot corresponds to the element of maximum absolute value among the remaining, to be factorized rows. This pivoting strategy requires the element type to also support [`abs`](@ref) and [`<`](@ref). (This is generally the only numerically stable option for floating-point matrices.)
  * `RowNonZero()`: the pivot corresponds to the first non-zero element among the remaining, to be factorized rows.  (This corresponds to the typical choice in hand calculations, and is also useful for more general algebraic number types that support [`iszero`](@ref) but not `abs` or `<`.)
  * `NoPivot()`: pivoting turned off (may fail if a zero entry is encountered).

The individual components of the factorization `F` can be accessed via [`getproperty`](@ref):

| Component | Description                         |
|:--------- |:----------------------------------- |
| `F.L`     | `L` (lower triangular) part of `LU` |
| `F.U`     | `U` (upper triangular) part of `LU` |
| `F.p`     | (right) permutation `Vector`        |
| `F.P`     | (right) permutation `Matrix`        |

Iterating the factorization produces the components `F.L`, `F.U`, and `F.p`.

The relationship between `F` and `A` is

`F.L*F.U == A[F.p, :]`

`F` further supports the following functions:

| Supported function  | `LU` | `LU{T,Tridiagonal{T}}` |
|:------------------- |:---- |:---------------------- |
| [`/`](@ref)         | ✓    |                        |
| [`\`](@ref)         | ✓    | ✓                      |
| [`inv`](@ref)       | ✓    | ✓                      |
| [`det`](@ref)       | ✓    | ✓                      |
| [`logdet`](@ref)    | ✓    | ✓                      |
| [`logabsdet`](@ref) | ✓    | ✓                      |
| [`size`](@ref)      | ✓    | ✓                      |

# Examples

```jldoctest
julia> A = [4 3; 6 3]
2×2 Matrix{Int64}:
 4  3
 6  3

julia> F = lu(A)
LU{Float64, Matrix{Float64}, Vector{Int64}}
L factor:
2×2 Matrix{Float64}:
 1.0       0.0
 0.666667  1.0
U factor:
2×2 Matrix{Float64}:
 6.0  3.0
 0.0  1.0

julia> F.L * F.U == A[F.p, :]
true

julia> l, u, p = lu(A); # destructuring via iteration

julia> l == F.L && u == F.U && p == F.p
true
```
