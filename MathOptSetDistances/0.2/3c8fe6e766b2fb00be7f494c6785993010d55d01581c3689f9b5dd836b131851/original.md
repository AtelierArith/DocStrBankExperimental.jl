```
projection_on_set(::DefaultDistance, v::AbstractVector{T}, ::MOI.PositiveSemidefiniteConeTriangle) where {T}
```

Projection of vector `v` on symmetric positive semidefinite cone i.e. `K = S^n⨥`

```
projection_on_set(::DefaultDistance, v::AbstractVector{T}, ::MOI.HermitianPositiveSemidefiniteConeTriangle) where {T}
```

Projection of vector `v` on hermitian positive semidefinite cone.
