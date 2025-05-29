```
kpm_mul(A, kpm_expansion::KPMExpansion, v::T) where {T<:AbstractVecOrMat}
```

Evaluate and return the vector $v^\prime = F(A) \cdot v$ where $F(A)$ is represented by the Chebyshev expansion. For more information refer to [`kpm_mul!`](@ref).
