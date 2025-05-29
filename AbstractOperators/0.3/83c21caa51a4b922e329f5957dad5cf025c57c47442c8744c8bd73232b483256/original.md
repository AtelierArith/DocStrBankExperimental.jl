`is_orthogonal(A::AbstractOperator)`

Test whether `A` is orthogonal.

```julia
julia> is_orthogonal(DCT(10))
true

julia> is_orthogonal(MatrixOp(randn(3,4)))
false

```
