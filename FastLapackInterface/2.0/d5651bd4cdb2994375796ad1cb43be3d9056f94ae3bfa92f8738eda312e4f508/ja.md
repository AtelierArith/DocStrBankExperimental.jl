```
HermitianEigenWs
```

エルミート対角化に使用されるワークスペースで、[`LAPACK.syevr!`](@ref) 関数を使用します。`Real` および `Complex` エルミート行列の両方をサポートしています。

# 例

```jldoctest
julia> A = [1.2 2.3
            6.2 3.3]
2×2 Matrix{Float64}:
 1.2  2.3
 6.2  3.3

julia> ws = HermitianEigenWs(A, vecs=true)
HermitianEigenWs{Float64, Matrix{Float64}, Float64}
  work: 66-element Vector{Float64}
  rwork: 0-element Vector{Float64}
  iwork: 20-element Vector{Int64}
  w: 2-element Vector{Float64}
  Z: 2×2 Matrix{Float64}
  isuppz: 4-element Vector{Int64}


julia> LinearAlgebra.Eigen(LAPACK.syevr!(ws, 'V', 'A', 'U', A, 0.0, 0.0, 0, 0, 1e-6)...)
Eigen{Float64, Float64, Matrix{Float64}, Vector{Float64}}
values:
2-element Vector{Float64}:
 -0.2783393759541063
  4.778339375954106
vectors:
2×2 Matrix{Float64}:
 -0.841217  0.540698
  0.540698  0.841217
```
