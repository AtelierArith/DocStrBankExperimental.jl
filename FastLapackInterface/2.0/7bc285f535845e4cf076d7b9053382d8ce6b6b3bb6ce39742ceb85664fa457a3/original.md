```
EigenWs
```

Workspace for [`LinearAlgebra.Eigen`](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/#LinearAlgebra.Eigen) factorization using the [`LAPACK.geevx!`](@ref) function.

# Examples

```jldoctest
julia> A = [1.2 2.3
            6.2 3.3]
2×2 Matrix{Float64}:
 1.2  2.3
 6.2  3.3

julia> ws = EigenWs(A, rvecs=true)
EigenWs{Float64, Matrix{Float64}, Float64}
  work: 260-element Vector{Float64}
  rwork: 2-element Vector{Float64}
  VL: 0×2 Matrix{Float64}
  VR: 2×2 Matrix{Float64}
  W: 2-element Vector{Float64}
  scale: 2-element Vector{Float64}
  iwork: 0-element Vector{Int64}
  rconde: 0-element Vector{Float64}
  rcondv: 0-element Vector{Float64}


julia> t = LAPACK.geevx!(ws, 'N', 'N', 'V', 'N', A);

julia> LinearAlgebra.Eigen(t[2], t[5])
Eigen{Float64, Float64, Matrix{Float64}, Vector{Float64}}
values:
2-element Vector{Float64}:
 -1.6695025194532018
  6.169502519453203
vectors:
2×2 Matrix{Float64}:
 -0.625424  -0.420019
  0.780285  -0.907515
```
