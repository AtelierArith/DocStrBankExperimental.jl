```
mul!(Y::AbstractVecOrMat, A::LinearMap, B::AbstractVector) -> Y
mul!(Y::AbstractMatrix, A::LinearMap, B::AbstractMatrix) -> Y
```

Calculates the action of the linear map `A` on the vector or matrix `B` and stores the result in `Y`, overwriting the existing value of `Y`. Note that `Y` must not be aliased with either `A` or `B`.

## Examples

```jldoctest; setup=(using LinearAlgebra, LinearMaps)
julia> A = LinearMap([1.0 2.0; 3.0 4.0]); B = ones(2); Y = similar(B); mul!(Y, A, B)
2-element Vector{Float64}:
 3.0
 7.0

julia> A = LinearMap([1.0 2.0; 3.0 4.0]); B = ones(2,2); Y = similar(B); mul!(Y, A, B)
2×2 Matrix{Float64}:
 3.0  3.0
 7.0  7.0
```
