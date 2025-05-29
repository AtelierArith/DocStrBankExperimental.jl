`Ax_mul_Bx(A::AbstractOperator,B::AbstractOperator)`

演算子 `P` を作成します：

`P*x == (Ax)*(Bx)`

# 例

```julia
julia> A,B = randn(4,4),randn(4,4);

julia> P = Ax_mul_Bx(MatrixOp(A,4),MatrixOp(B,4))
▒*▒  ℝ^4 -> ℝ^(4, 4)

julia> X = randn(4,4);

julia> P*X == (A*X)*(B*X)
true

```
