`HadamardProd(A::AbstractOperator,B::AbstractOperator)`

演算子 `P` を作成します：

`P*x == (Ax).*(Bx)`

# 例

```julia
julia> A,B = Sin(3), Cos(3);

julia> P = HadamardProd(A,B)
sin.*cos  ℝ^3 -> ℝ^3

julia> x = randn(3);

julia> P*x == (sin.(x).*cos.(x))
true
```
