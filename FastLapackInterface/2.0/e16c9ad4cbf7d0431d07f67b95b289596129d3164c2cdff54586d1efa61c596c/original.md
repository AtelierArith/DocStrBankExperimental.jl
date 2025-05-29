```
QRWYWs
```

Workspace to be used with the [`LinearAlgebra.QRCompactWY`](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/#LinearAlgebra.QRCompactWY) representation of the blocked QR factorization which uses the [`LAPACK.geqrt!`](@ref) function. By default the blocksize for the algorithm is taken as `min(36, min(size(template)))`, this can be overridden by using the `blocksize` keyword of the constructor.

# Examples

```jldoctest
julia> A = [1.2 2.3
            6.2 3.3]
2×2 Matrix{Float64}:
 1.2  2.3
 6.2  3.3

julia> ws = QRWYWs(A)
QRWYWs{Float64, Matrix{Float64}}
  work: 4-element Vector{Float64}
  T: 2×2 Matrix{Float64}

julia> t = LinearAlgebra.QRCompactWY(LAPACK.geqrt!(ws, A)...)
LinearAlgebra.QRCompactWY{Float64, Matrix{Float64}, Matrix{Float64}}
Q factor: 2×2 LinearAlgebra.QRCompactWYQ{Float64, Matrix{Float64}, Matrix{Float64}}
R factor:
2×2 Matrix{Float64}:
 -6.31506  -3.67692
  0.0      -1.63102

julia> Matrix(t)
2×2 Matrix{Float64}:
 1.2  2.3
 6.2  3.3
```
