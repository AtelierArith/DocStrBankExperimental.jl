```
Workspace(lapack_function, A)
```

Will create the correct [`Workspace`](@ref WorkSpaces) for the target `lapack_function` and matrix `A`.

# Examples

```jldoctest
julia> A = [1.2 2.3
            6.2 3.3]
2×2 Matrix{Float64}:
 1.2  2.3
 6.2  3.3

julia> ws = Workspace(LAPACK.geqrt!, A)
QRWYWs{Float64, Matrix{Float64}}
  work: 4-element Vector{Float64}
  T: 2×2 Matrix{Float64}


julia> LinearAlgebra.QRCompactWY(factorize!(ws, A)...)
LinearAlgebra.QRCompactWY{Float64, Matrix{Float64}, Matrix{Float64}}
Q factor: 2×2 LinearAlgebra.QRCompactWYQ{Float64, Matrix{Float64}, Matrix{Float64}}
R factor:
2×2 Matrix{Float64}:
 -6.31506  -3.67692
  0.0      -1.63102
```
