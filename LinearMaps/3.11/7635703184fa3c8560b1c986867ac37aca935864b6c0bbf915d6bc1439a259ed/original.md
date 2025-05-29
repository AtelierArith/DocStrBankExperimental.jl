```
*(A::LinearMap, X::Union{AbstractMatrix,AbstractQ})::CompositeMap
```

Return the `CompositeMap` `A*LinearMap(X)`, interpreting the matrix `X` as a linear operator, rather than a collection of column vectors. To compute the action of `A` on each column of `X`, call `Matrix(A*X)` or use the in-place multiplication `mul!(Y, A, X[, α, β])` with an appropriately sized, preallocated matrix `Y`.

## Examples

```jldoctest; setup=(using LinearMaps)
julia> A=LinearMap([1.0 2.0; 3.0 4.0]); X=[1.0 1.0; 1.0 1.0];

julia> A*X isa LinearMaps.CompositeMap
true
```
