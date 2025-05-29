```
kpm_lmul!(
    A, coefs::AbstractVector, v::T, bounds,
    tmp = zeros(eltype(v), size(v)..., 3)
) where {T<:AbstractVecOrMat}
```

Evaluates $v = F(A) \cdot v$, modifying $v$ in-place, where $F(A)$ is represented by the Chebyshev expansion. Here `A` is either a function that can be called as `A(u,v)` to evaluate $u = A\cdot v$, modifying `u` in-place, or is a type for which the operation `mul!(u, A, v)` is defined. The vector `coefs` contains Chebyshev expansion coefficients to approximate $F(A)$, where the eigenspectrum of $A$ is contained in the interval `(bounds[1], bounds[2])` specified by the `bounds` argument. The vector `v` is vector getting multiplied by the Chebyshev expansion for $F(A)$. Lastly, `tmp` is an array used to avoid dynamic memory allocations.
