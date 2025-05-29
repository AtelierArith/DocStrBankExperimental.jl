```
kpm_mul!(
    v′::T, A, kpm_expansion::KPMExpansion, v::T,
    tmp = zeros(eltype(v), size(v)..., 3)
) where {T<:AbstractVecOrMat}
```

Evaluates $v^\prime = F(A) \cdot v$, writing the result to $v^\prime$, where $F(A)$ is represented by the Chebyshev expansion. Here `A` is either a function that can be called as `A(u,v)` to evaluate $u = A\cdot v$, modifying `u` in-place, or is a type for which the operation `mul!(u, A, v)` is defined. Lastly, the array `tmp` is used to avoid dynamic memory allocations.
