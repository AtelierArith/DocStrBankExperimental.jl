```
reshape_vector(vectorized_form::Vector, shape::AbstractShape)
```

Return an object in its original shape `shape` given its vectorized form `vectorized_form`.

## Examples

Given a [`SymmetricMatrixShape`](@ref) of vectorized form `[1, 2, 3]`, the following code returns the matrix `Symmetric(Matrix[1 2; 2 3])`:

```jldoctest; setup = :(using JuMP)
julia> reshape_vector([1, 2, 3], SymmetricMatrixShape(2))
2×2 LinearAlgebra.Symmetric{Int64,Array{Int64,2}}:
 1  2
 2  3
```
