```
mul!(Y::AbstractMatrix, A::LinearMap, b::Number) -> Y
```

Scales the matrix representation of the linear map `A` by `b` and stores the result in `Y`, overwriting the existing value of `Y`.

## Examples

```jldoctest; setup=(using LinearAlgebra, LinearMaps)
julia> A = LinearMap{Int}(cumsum, 3); b = 2; Y = Matrix{Int}(undef, (3,3));

julia> mul!(Y, A, b)
3×3 Matrix{Int64}:
 2  0  0
 2  2  0
 2  2  2
```
