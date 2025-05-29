`Jacobian(A::AbstractOperator,x)`

ショートハンドコンストラクタ: 

`jacobian(A::AbstractOperator,x)`

`A`のジャコビアンを`x`で評価した結果を返します（`LinearOperator`の場合は`A`自体になります）。

```julia
julia> Jacobian(DFT(10),randn(10))
ℱ  ℝ^10 -> ^ℂ10

julia> Jacobian(Sigmoid((10,)),randn(10))
J(σ)  ℝ^10 -> ℝ^10

```
