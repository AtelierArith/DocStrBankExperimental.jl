```
QRPivotedWs
```

Workspace to be used with the [`LinearAlgebra.QRPivoted`](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/#LinearAlgebra.QRPivoted) representation of the QR factorization which uses the [`LAPACK.geqp3!`](@ref) function.

# Examples

```jldoctest
julia> A = [1.2 2.3
            6.2 3.3]
2×2 Matrix{Float64}:
 1.2  2.3
 6.2  3.3

julia> ws = QRPivotedWs(A)
QRPivotedWs{Float64, Float64}
  work: 100-element Vector{Float64}
  rwork: 0-element Vector{Float64}
  τ: 2-element Vector{Float64}
  jpvt: 2-element Vector{Int64}

julia> t = QRPivoted(LAPACK.geqp3!(ws, A)...)
QRPivoted{Float64, Matrix{Float64}, Vector{Float64}, Vector{Int64}}
Q factor: 2×2 LinearAlgebra.QRPackedQ{Float64, Matrix{Float64}, Vector{Float64}}
R factor:
2×2 Matrix{Float64}:
 -6.31506  -3.67692
  0.0      -1.63102
permutation:
2-element Vector{Int64}:
 1
 2

julia> Matrix(t)
2×2 Matrix{Float64}:
 1.2  2.3
 6.2  3.3
```
