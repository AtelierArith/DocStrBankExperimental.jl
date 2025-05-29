```
QROrgWs
```

[`LinearAlgebra.LAPACK.orgqr!`](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/#LinearAlgebra.LAPACK.orgqr!) 関数で使用されるワークスペース。これは、以前の因子分解の `QR` または `QRPivoted` のワークスペースを必要とします。

# 例

```jldoctest julia> A = [1.2 2.3             6.2 3.3] 2×2 Matrix{Float64}:  1.2  2.3  6.2  3.3

julia> ws = QRPivotedWs(A) QRPivotedWs{Float64, Float64}   work: 100-element Vector{Float64}   rwork: 0-element Vector{Float64}   τ: 2-element Vector{Float64}   jpvt: 2-element Vector{Int64}

julia> C=[1 0.5; 2 1] 2×2 Matrix{Float64}:  1.0  0.5  2.0  1.0

julia> orgws =  QROrgWs(ws, 'L', 'N', A, C) QROrgWs{Float64}   work: 4224-element Vector{Float64}   τ: 2-element Vector{Float64}
```
