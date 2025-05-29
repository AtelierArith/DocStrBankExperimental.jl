```
GeneralizedEigenWs
```

Workspace that can be used for [`LinearAlgebra.GeneralizedEigen`](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/#LinearAlgebra.GeneralizedEigen) factorization using [`LAPACK.ggev!`](@ref). Supports `Real` and `Complex` matrices.

# Examples

```jldoctest
julia> A = [1.2 2.3
            6.2 3.3]
2×2 Matrix{Float64}:
 1.2  2.3
 6.2  3.3

julia> B = [8.2 1.7
            5.9 2.1]
2×2 Matrix{Float64}:
 8.2  1.7
 5.9  2.1

julia> ws = GeneralizedEigenWs(A, rvecs=true)
GeneralizedEigenWs{Float64, Matrix{Float64}, Float64}
  work: 78-element Vector{Float64}
  vl: 0×2 Matrix{Float64}
  vr: 2×2 Matrix{Float64}
  αr: 2-element Vector{Float64}
  αi: 2-element Vector{Float64}
  β: 2-element Vector{Float64}


julia> αr, αi, β, _, vr = LAPACK.ggev!(ws, 'N', 'V', A, B);

julia> LinearAlgebra.GeneralizedEigen(αr ./ β, vr)
GeneralizedEigen{Float64, Float64, Matrix{Float64}, Vector{Float64}}
values:
2-element Vector{Float64}:
 -0.8754932558185097
  1.6362721153456299
vectors:
2×2 Matrix{Float64}:
 -0.452121  -0.0394242
  1.0        1.0
```
