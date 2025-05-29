```
QRPivotedWs
```

[`LinearAlgebra.QRPivoted`](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/#LinearAlgebra.QRPivoted) 表現を使用するためのワークスペースで、QR因子分解において [`LAPACK.geqp3!`](@ref) 関数を使用します。

# 例

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
Q因子: 2×2 LinearAlgebra.QRPackedQ{Float64, Matrix{Float64}, Vector{Float64}}
R因子:
2×2 Matrix{Float64}:
 -6.31506  -3.67692
  0.0      -1.63102
置換:
2-element Vector{Int64}:
 1
 2

julia> Matrix(t)
2×2 Matrix{Float64}:
 1.2  2.3
 6.2  3.3
```
