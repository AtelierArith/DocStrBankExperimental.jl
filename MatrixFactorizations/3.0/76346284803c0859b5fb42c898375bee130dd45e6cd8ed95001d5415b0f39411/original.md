```
ql(A, pivot=Val(false)) -> F
```

Compute the QL factorization of the matrix `A`: an orthogonal (or unitary if `A` is complex-valued) matrix `Q`, and a lower triangular matrix `L` such that

$$
A = Q L
$$

The returned object `F` stores the factorization in a packed format:

  * `F` is a [`QL`](@ref) object.

The individual components of the decomposition `F` can be retrieved via property accessors:

  * `F.Q`: the orthogonal/unitary matrix `Q`
  * `F.L`: the lower triangular matrix `L`

Iterating the decomposition produces the components `Q`, `L`, and if extant `p`.

The following functions are available for the `QL` objects: [`inv`](@ref), [`size`](@ref), and [`\`](@ref). When `A` is rectangular, `\` will return a least squares solution and if the solution is not unique, the one with smallest norm is returned. When `A` is not full rank, factorization with (column) pivoting is required to obtain a minimum norm solution.

Multiplication with respect to either full/square or non-full/square `Q` is allowed, i.e. both `F.Q*F.L` and `F.Q*A` are supported. A `Q` matrix can be converted into a regular matrix with [`Matrix`](@ref).  This operation returns the "thin" Q factor, i.e., if `A` is `m`×`n` with `m>=n`, then `Matrix(F.Q)` yields an `m`×`n` matrix with orthonormal columns.  To retrieve the "full" Q factor, an `m`×`m` orthogonal matrix, use `F.Q*Matrix(I,m,m)`.  If `m<=n`, then `Matrix(F.Q)` yields an `m`×`m` orthogonal matrix.

# Examples

```jldoctest
julia> A = [3.0 -6.0; 4.0 -8.0; 0.0 1.0]
3×2 Array{Float64,2}:
 3.0  -6.0
 4.0  -8.0
 0.0   1.0

julia> F = ql(A)
LinearAlgebra.QLCompactWY{Float64,Array{Float64,2}}
Q factor:
3×3 LinearAlgebra.QLCompactWYQ{Float64,Array{Float64,2}}:
 -0.6   0.0   0.8
 -0.8   0.0  -0.6
  0.0  -1.0   0.0
L factor:
2×2 Array{Float64,2}:
 -5.0  10.0
  0.0  -1.0

julia> F.Q * F.L == A
true
```
