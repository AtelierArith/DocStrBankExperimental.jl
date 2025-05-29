```
CholeskyPivotedWs
```

[`LinearAlgebra.CholeskyPivoted`](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/#LinearAlgebra.CholeskyPivoted) 因数分解のためのワークスペースで、[`LAPACK.pstrf!`](@ref) 関数を使用します。標準の [`LinearAlgebra.Cholesky`](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/#LinearAlgebra.Cholesky) は、[`LAPACK.potrf!`](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/#LinearAlgebra.LAPACK.potrf!) を使用しており、これはメモリを割り当てず、別の [`Workspace`](@ref) を必要としません。

# 例

```jldoctest
julia> A = [1.2 7.8
            7.8 3.3]
2×2 Matrix{Float64}:
 1.2  7.8
 7.8  3.3

julia> ws = CholeskyPivotedWs(A)
CholeskyPivotedWs{Float64}
  work: 4-element Vector{Float64}
  piv: 2-element Vector{Int64}


julia> AA, piv, rank, info = LAPACK.pstrf!(ws, 'U', A, 1e-6)
([1.816590212458495 4.293758683992806; 7.8 -17.236363636363635], [2, 1], 1, 1)

julia> CholeskyPivoted(AA, 'U', piv, rank, 1e-6, info)
CholeskyPivoted{Float64, Matrix{Float64}, Vector{Int64}}
U因子のランク 1:
2×2 UpperTriangular{Float64, Matrix{Float64}}:
 1.81659    4.29376
  ⋅       -17.2364
置換:
2-element Vector{Int64}:
 2
 1
```
