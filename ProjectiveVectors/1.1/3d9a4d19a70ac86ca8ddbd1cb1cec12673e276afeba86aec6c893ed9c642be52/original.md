```
LinearAlgebra.rmul!(z::PVector{T, N}, λ::NTuple{N, <:Number}) where {T, N}
LinearAlgebra.rmul!(z::PVector{T, 1}, λ::Number) where {T}
```

Multiply each component of `zᵢ` of `z` by `λ[i]`.
