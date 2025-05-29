```
kpm_mul(
    A, coefs::AbstractVector, bounds, v::T, tmp = zeros(eltype(v), size(v)..., 3)
) where {T<:AbstractVecOrMat}
```

Evaluate and return the vector $v^\prime = F(A) \cdot v$ where $F(A)$ is represented by the Chebyshev expansion. For more information refer to [`kpm_mul!`](@ref).
