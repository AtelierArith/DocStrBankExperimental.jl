`Axt_mul_Bx(A::AbstractOperator,B::AbstractOperator)`

演算子 `P` を作成します：

`P*x == (Ax)'*(Bx)`

# 例

```julia
julia> A,B = randn(4,4),randn(4,4);

julia> P = Axt_mul_Bx(MatrixOp(A),MatrixOp(B))
▒*▒  ℝ^4 -> ℝ^1

julia> x = randn(4);

julia> P*x == [(A*x)'*(B*x)]
true

```
