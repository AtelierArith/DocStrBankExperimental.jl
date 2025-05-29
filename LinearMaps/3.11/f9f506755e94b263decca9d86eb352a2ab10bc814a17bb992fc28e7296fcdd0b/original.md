```
*(X::Union{AbstractMatrix,AbstractQ}, A::LinearMap)::CompositeMap
```

Return the `CompositeMap` `LinearMap(X)*A`, interpreting the matrix `X` as a linear operator. To compute the right-action of `A` on each row of `X`, call `Matrix(X*A)` or `mul!(Y, X, A)` for the in-place version.

## Examples

```jldoctest; setup=(using LinearMaps)
julia> X=[1.0 1.0; 1.0 1.0]; A=LinearMap([1.0 2.0; 3.0 4.0]);

julia> X*A isa LinearMaps.CompositeMap
true
```
