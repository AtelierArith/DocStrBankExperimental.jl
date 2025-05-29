```
BunchKaufmanWs
```

[`LinearAlgebra.BunchKaufman`](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/#LinearAlgebra.BunchKaufman) 因数分解のためのワークスペースで、対称行列には [`LAPACK.sytrf!`](@ref) または [`LAPACK.sytrf_rook!`](@ref) 関数を、エルミート行列には [`LAPACK.hetrf!`](@ref) または [`LAPACK.hetrf_rook!`](@ref) 関数を使用します（例：`ComplexF64` または `ComplexF32` 要素を持つ行列）。

# 例

```jldoctest
julia> A = [1.2 7.8
            7.8 3.3]
2×2 Matrix{Float64}:
 1.2  7.8
 7.8  3.3

julia> ws = BunchKaufmanWs(A)
BunchKaufmanWs{Float64}
  work: 128-element Vector{Float64}
  ipiv: 2-element Vector{Int64}


julia> A, ipiv, info = LAPACK.sytrf!(ws, 'U', A)
([1.2 7.8; 7.8 3.3], [-1, -1], 0)

julia> t = LinearAlgebra.BunchKaufman(A, ipiv,'U', true, false, info)
BunchKaufman{Float64, Matrix{Float64}, Vector{Int64}}
D factor:
2×2 Tridiagonal{Float64, Vector{Float64}}:
 1.2  7.8
 7.8  3.3
U factor:
2×2 UnitUpperTriangular{Float64, Matrix{Float64}}:
 1.0  0.0
  ⋅   1.0
permutation:
2-element Vector{Int64}:
 1
 2

julia> A = [1.2 7.8
            7.8 3.3]
2×2 Matrix{Float64}:
 1.2  7.8
 7.8  3.3

julia> ws = BunchKaufmanWs(A)
BunchKaufmanWs{Float64}
  work: 128-element Vector{Float64}
  ipiv: 2-element Vector{Int64}


julia> A, ipiv, info = LAPACK.sytrf_rook!(ws, 'U', A)
([1.2 7.8; 7.8 3.3], [-1, -2], 0)

julia> t = LinearAlgebra.BunchKaufman(A, ipiv,'U', true, true, info)
BunchKaufman{Float64, Matrix{Float64}, Vector{Int64}}
D factor:
2×2 Tridiagonal{Float64, Vector{Float64}}:
 1.2  7.8
 7.8  3.3
U factor:
2×2 UnitUpperTriangular{Float64, Matrix{Float64}}:
 1.0  0.0
  ⋅   1.0
permutation:
2-element Vector{Int64}:
 1
 2
```
