```
LUWs
```

Workspace to be used with the [`LinearAlgebra.LU`](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/#LinearAlgebra.LU) representation of the LU factorization which uses the [`LAPACK.getrf!`](@ref) function.

# Examples

```jldoctest
julia> A = [1.2 2.3
            6.2 3.3]
2×2 Matrix{Float64}:
 1.2  2.3
 6.2  3.3

julia> ws = LUWs(A)
LUWs
  ipiv: 2-element Vector{Int64}

julia> t = LU(LAPACK.getrf!(ws, A)...)
LU{Float64, Matrix{Float64}, Vector{Int64}}
L factor:
2×2 Matrix{Float64}:
 1.0       0.0
 0.193548  1.0
U factor:
2×2 Matrix{Float64}:
 6.2  3.3
 0.0  1.66129
```
