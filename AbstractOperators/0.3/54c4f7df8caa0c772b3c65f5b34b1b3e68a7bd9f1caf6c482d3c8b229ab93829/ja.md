`Reshape(A::AbstractOperator, dim_out...)`

ショートハンドコンストラクタ: 

`reshape(A, idx...)` 

`AbstractOperator`のコドメイン次元を再形成します。

```julia
julia> A = Reshape(DFT(10),2,5)
¶ℱ  ℝ^10 -> ℂ^(2, 5)

julia> R = reshape(Conv((19,),randn(10)),7,2,2)
¶★  ℝ^19 -> ℝ^(7, 2, 2)

```
