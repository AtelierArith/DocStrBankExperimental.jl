`Compose(A::AbstractOperator,B::AbstractOperator)`

Shorthand constructor: 

`A*B` 

Compose different `AbstractOperator`s. Notice that the domain and codomain of the operators `A` and `B` must match, i.e. `size(A,2) == size(B,1)` and `domainType(A) == codomainType(B)`.

```julia
julia> Compose(DFT(16,2),Variation((4,4)))
ℱc*Ʋ  ℝ^(4, 4) -> ℝ^(16, 2)

julia> MatrixOp(randn(20,10))*DCT(10)
▒*ℱc  ℝ^10 -> ℝ^20

```
