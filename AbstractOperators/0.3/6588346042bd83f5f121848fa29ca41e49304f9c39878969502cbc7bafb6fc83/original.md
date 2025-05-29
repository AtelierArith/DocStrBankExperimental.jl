`AdjointOperator(A::AbstractOperator)`

Shorthand constructor: 

`'(A::AbstractOperator)`

Returns the adjoint operator of `A`.

```julia
julia> AdjointOperator(DFT(10))
ℱᵃ  ℂ^10 -> ℝ^10

julia> [DFT(10); DCT(10)]'
[ℱ;ℱc]ᵃ  ℂ^10  ℝ^10 -> ℝ^10
```
