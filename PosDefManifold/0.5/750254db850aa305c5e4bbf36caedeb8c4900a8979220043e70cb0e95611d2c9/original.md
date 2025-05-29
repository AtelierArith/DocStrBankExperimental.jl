```
colNorm(X::Union{𝕄{T}, ℍ{T}}, j::Int) where T<:RealOrComplex
```

Given a real or complex `Matrix` or `Hermitian` matrix $X$,  return the Euclidean norm of its $j^{th}$ column.

This function calls the  [BLAS.nrm2](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/#LinearAlgebra.BLAS.nrm2)  routine. See [Threads](@ref).

**See also**: [`normalizeCol!`](@ref), [`colProd`](@ref), [`sumOfSqr`](@ref).

**Examples**

```julia
using PosDefManifold
X=randn(10, 20)
normOfSecondColumn=colNorm(X, 2)
```
