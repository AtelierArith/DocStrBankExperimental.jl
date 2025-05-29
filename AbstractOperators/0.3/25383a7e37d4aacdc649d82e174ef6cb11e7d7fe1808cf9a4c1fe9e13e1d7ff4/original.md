`Ax_mul_Bxt(A::AbstractOperator,B::AbstractOperator)`

Create an operator `P` such that:

`P == (Ax)*(Bx)'`

# Example: Matrix multiplication

```julia
julia> A,B = randn(4,4),randn(4,4);

julia> P = Ax_mul_Bxt(MatrixOp(A),MatrixOp(B))
▒*▒  ℝ^4 -> ℝ^(4, 4)

julia> x = randn(4);

julia> P*x == (A*x)*(B*x)'
true

```
