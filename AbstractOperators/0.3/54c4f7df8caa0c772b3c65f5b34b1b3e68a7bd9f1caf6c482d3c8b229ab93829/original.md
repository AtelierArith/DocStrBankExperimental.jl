`Reshape(A::AbstractOperator, dim_out...)`

Shorthand constructor: 

`reshape(A, idx...)` 

Reshape the codomain dimensions of an `AbstractOperator`.

```julia
julia> A = Reshape(DFT(10),2,5)
¶ℱ  ℝ^10 -> ℂ^(2, 5)

julia> R = reshape(Conv((19,),randn(10)),7,2,2)
¶★  ℝ^19 -> ℝ^(7, 2, 2)

```
