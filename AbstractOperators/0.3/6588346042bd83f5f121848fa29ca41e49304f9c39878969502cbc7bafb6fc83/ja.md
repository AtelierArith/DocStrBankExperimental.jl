`AdjointOperator(A::AbstractOperator)`

省略構文コンストラクタ: 

`'(A::AbstractOperator)`

`A`の随伴演算子を返します。

```julia
julia> AdjointOperator(DFT(10))
ℱᵃ  ℂ^10 -> ℝ^10

julia> [DFT(10); DCT(10)]'
[ℱ;ℱc]ᵃ  ℂ^10  ℝ^10 -> ℝ^10
```
