```
projection_on_set(::DefaultDistance, v::AbstractVector{T}, ::MOI.PositiveSemidefiniteConeTriangle) where {T}
```

ベクトル `v` の対称正定値円錐への射影、すなわち `K = S^n⨥`

```
projection_on_set(::DefaultDistance, v::AbstractVector{T}, ::MOI.HermitianPositiveSemidefiniteConeTriangle) where {T}
```

ベクトル `v` のエルミート正定値円錐への射影。 ```
