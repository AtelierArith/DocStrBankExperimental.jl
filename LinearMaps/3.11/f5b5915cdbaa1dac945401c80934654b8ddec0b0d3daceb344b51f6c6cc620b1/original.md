```
mul!(Y::AbstractMatrix, A::LinearMap, b::Number, α::Number, β::Number) -> Y
```

Scales the matrix representation of the linear map `A` by `b*α`, adds the result to `Y*β` and stores the final result in `Y`, overwriting the existing value of `Y`.

## Examples

```jldoctest; setup=(using LinearAlgebra, LinearMaps)
julia> A = LinearMap{Int}(cumsum, 3); b = 2; Y = ones(Int, (3,3));

julia> mul!(Y, A, b, 2, 1)
3×3 Matrix{Int64}:
 5  1  1
 5  5  1
 5  5  5
```
