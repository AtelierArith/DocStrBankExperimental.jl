`Ax_mul_Bxt(A::AbstractOperator,B::AbstractOperator)`

演算子 `P` を作成します：

`P == (Ax)*(Bx)'`

# 例: 行列の積

```julia
julia> A,B = randn(4,4),randn(4,4);

julia> P = Ax_mul_Bxt(MatrixOp(A),MatrixOp(B))
▒*▒  ℝ^4 -> ℝ^(4, 4)

julia> x = randn(4);

julia> P*x == (A*x)*(B*x)'
true

```
