```
kernelmatrix!(K::AbstractMatrix, κ::Kernel, x::AbstractVector)
kernelmatrix!(K::AbstractMatrix, κ::Kernel, x::AbstractVector, y::AbstractVector)
```

In-place version of [`kernelmatrix`](@ref) where pre-allocated matrix `K` will be overwritten with the kernel matrix.

```
kernelmatrix!(K::AbstractMatrix, κ::Kernel, X::AbstractMatrix; obsdim)
kernelmatrix!(
    K::AbstractMatrix,
    κ::Kernel,
    X::AbstractMatrix,
    Y::AbstractMatrix;
    obsdim,
)
```

If `obsdim=1`, equivalent to `kernelmatrix!(K, κ, RowVecs(X))` and `kernelmatrix(K, κ, RowVecs(X), RowVecs(Y))`, respectively. If `obsdim=2`, equivalent to `kernelmatrix!(K, κ, ColVecs(X))` and `kernelmatrix(K, κ, ColVecs(X), ColVecs(Y))`, respectively.

See also: [`ColVecs`](@ref), [`RowVecs`](@ref)
