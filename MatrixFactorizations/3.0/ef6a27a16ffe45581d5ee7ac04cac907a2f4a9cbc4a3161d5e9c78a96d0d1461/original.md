```
UL <: Factorization
```

Matrix factorization type of the `UL` factorization of a square matrix `A`. This is the return type of [`ul`](@ref), the corresponding matrix factorization function.

The individual components of the factorization `F::UL` can be accessed via [`getproperty`](@ref):

| Component | Description                              |
|:--------- |:---------------------------------------- |
| `F.U`     | `U` (upper triangular) part of `UL`      |
| `F.L`     | `L` (unit lower triangular) part of `UL` |
| `F.p`     | (right) permutation `Vector`             |
| `F.P`     | (right) permutation `Matrix`             |

Iterating the factorization produces the components `F.U`, `F.L`, and `F.p`.

# Examples

```jldoctest
julia> A = [4 3; 6 3]
2×2 Array{Int64,2}:
 4  3
 6  3

julia> F = ul(A)
UL{Float64,Array{Float64,2}}
L factor:
2×2 Array{Float64,2}:
 1.0       0.0
 0.666667  1.0
U factor:
2×2 Array{Float64,2}:
 6.0  3.0
 0.0  1.0

julia> F.L * F.U == A[F.p, :]
true

julia> l, u, p = ul(A); # destructuring via iteration

julia> l == F.L && u == F.U && p == F.p
true
```
