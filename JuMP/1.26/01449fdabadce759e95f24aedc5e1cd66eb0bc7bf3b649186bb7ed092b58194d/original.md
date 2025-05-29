```
reshape_set(vectorized_set::MOI.AbstractSet, shape::AbstractShape)
```

Return a set in its original shape `shape` given its vectorized form `vectorized_form`.

## Example

Given a [`SymmetricMatrixShape`](@ref) of vectorized form `[1, 2, 3] in MOI.PositiveSemidefinieConeTriangle(2)`, the following code returns the set of the original constraint `Symmetric(Matrix[1 2; 2 3]) in PSDCone()`:

```jldoctest
julia> reshape_set(MOI.PositiveSemidefiniteConeTriangle(2), SymmetricMatrixShape(2))
PSDCone()
```
