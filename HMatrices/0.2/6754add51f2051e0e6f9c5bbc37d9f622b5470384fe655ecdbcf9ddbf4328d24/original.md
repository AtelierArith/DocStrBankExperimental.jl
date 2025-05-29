```
abstract type AbstractKernelMatrix{T} <: AbstractMatrix{T}
```

Interface for abstract matrices represented through a kernel function `f`, target elements `X`, and source elements `Y`. The matrix entry `i,j` is given by `f(X[i],Y[j])`. Concrete subtypes should implement at least

```
`Base.getindex(K::AbstractKernelMatrix,i::Int,j::Int)`
```

If a more efficient implementation of `getindex(K,I::UnitRange,I::UnitRange)`, `getindex(K,I::UnitRange,j::Int)` and `getindex(adjoint(K),I::UnitRange,j::Int)` is available (e.g. with SIMD vectorization), implementing such methods can improve the speed of assembling an [`HMatrix`](@ref).
