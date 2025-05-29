```
QRWs
```

Workspace for standard [`LinearAlgebra.QR`](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/#LinearAlgebra.QR) factorization using the [`LAPACK.geqrf!`](@ref) function.

# Examples

```jldoctest
julia> A = [1.2 2.3
            6.2 3.3]
2×2 Matrix{Float64}:
 1.2  2.3
 6.2  3.3

julia> ws = QRWs(A)
QRWs{Float64}
  work: 64-element Vector{Float64}
  τ: 2-element Vector{Float64}

julia> t = QR(LAPACK.geqrf!(ws, A)...)
QR{Float64, Matrix{Float64}, Vector{Float64}}
Q factor: 2×2 LinearAlgebra.QRPackedQ{Float64, Matrix{Float64}, Vector{Float64}}
R factor:
2×2 Matrix{Float64}:
 -6.31506  -3.67692
  0.0      -1.63102

julia> Matrix(t)
2×2 Matrix{Float64}:
 1.2  2.3
 6.2  3.3
```
