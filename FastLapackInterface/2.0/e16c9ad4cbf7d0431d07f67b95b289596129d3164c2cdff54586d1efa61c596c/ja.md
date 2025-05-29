```
QRWYWs
```

[`LinearAlgebra.QRCompactWY`](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/#LinearAlgebra.QRCompactWY) 表現を使用したブロック QR 因数分解に使用されるワークスペースで、[`LAPACK.geqrt!`](@ref) 関数を使用します。デフォルトでは、アルゴリズムのブロックサイズは `min(36, min(size(template)))` として取られ、これはコンストラクタの `blocksize` キーワードを使用することで上書きできます。

# 例

```jldoctest
julia> A = [1.2 2.3
            6.2 3.3]
2×2 Matrix{Float64}:
 1.2  2.3
 6.2  3.3

julia> ws = QRWYWs(A)
QRWYWs{Float64, Matrix{Float64}}
  work: 4-element Vector{Float64}
  T: 2×2 Matrix{Float64}

julia> t = LinearAlgebra.QRCompactWY(LAPACK.geqrt!(ws, A)...)
LinearAlgebra.QRCompactWY{Float64, Matrix{Float64}, Matrix{Float64}}
Q 因子: 2×2 LinearAlgebra.QRCompactWYQ{Float64, Matrix{Float64}, Matrix{Float64}}
R 因子:
2×2 Matrix{Float64}:
 -6.31506  -3.67692
  0.0      -1.63102

julia> Matrix(t)
2×2 Matrix{Float64}:
 1.2  2.3
 6.2  3.3
```
