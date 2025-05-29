`is_invertible(A::AbstractOperator)`

Test whether `A` is easily invertible.

```julia
julia> is_invertible(DFT(10))
true

julia> is_invertible(MatrixOp(randn(3,4)))
false

```
