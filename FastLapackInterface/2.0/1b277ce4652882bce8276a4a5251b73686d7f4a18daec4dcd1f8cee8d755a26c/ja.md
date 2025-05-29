```
QRWs
```

標準の [`LinearAlgebra.QR`](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/#LinearAlgebra.QR) 因子分解のためのワークスペースで、[`LAPACK.geqrf!`](@ref) 関数を使用します。

# 例

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
Q 因子: 2×2 LinearAlgebra.QRPackedQ{Float64, Matrix{Float64}, Vector{Float64}}
R 因子:
2×2 Matrix{Float64}:
 -6.31506  -3.67692
  0.0      -1.63102

julia> Matrix(t)
2×2 Matrix{Float64}:
 1.2  2.3
 6.2  3.3
```
