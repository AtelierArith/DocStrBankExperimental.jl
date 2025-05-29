```
kernelmatrix_diag!(K::AbstractVector, κ::Kernel, x::AbstractVector)
kernelmatrix_diag!(K::AbstractVector, κ::Kernel, x::AbstractVector, y::AbstractVector)
```

In place version of [`kernelmatrix_diag`](@ref).

```
kernelmatrix_diag!(K::AbstractVector, κ::Kernel, X::AbstractMatrix; obsdim)
kernelmatrix_diag!(
    K::AbstractVector,
    κ::Kernel,
    X::AbstractMatrix,
    Y::AbstractMatrix;
    obsdim
)
```

If `obsdim=1`, equivalent to `kernelmatrix_diag!(K, κ, RowVecs(X))` and `kernelmatrix_diag!(K, κ, RowVecs(X), RowVecs(Y))`, respectively. If `obsdim=2`, equivalent to `kernelmatrix_diag!(K, κ, ColVecs(X))` and `kernelmatrix_diag!(K, κ, ColVecs(X), ColVecs(Y))`, respectively.

See also: [`ColVecs`](@ref), [`RowVecs`](@ref)
