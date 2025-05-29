```
kernelmatrix_diag(κ::Kernel, x::AbstractVector)
```

Compute the diagonal of `kernelmatrix(κ, x)` efficiently.

```
kernelmatrix_diag(κ::Kernel, x::AbstractVector, y::AbstractVector)
```

Compute the diagonal of `kernelmatrix(κ, x, y)` efficiently. Requires that `x` and `y` are the same length.

```
kernelmatrix_diag(κ::Kernel, X::AbstractMatrix; obsdim)
kernelmatrix_diag(κ::Kernel, X::AbstractMatrix, Y::AbstractMatrix; obsdim)
```

If `obsdim=1`, equivalent to `kernelmatrix_diag(κ, RowVecs(X))` and `kernelmatrix_diag(κ, RowVecs(X), RowVecs(Y))`, respectively. If `obsdim=2`, equivalent to `kernelmatrix_diag(κ, ColVecs(X))` and `kernelmatrix_diag(κ, ColVecs(X), ColVecs(Y))`, respectively.

See also: [`ColVecs`](@ref), [`RowVecs`](@ref)
