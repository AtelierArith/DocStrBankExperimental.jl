```
kernelmatrix(κ::Kernel, x::AbstractVector)
```

Compute the kernel `κ` for each pair of inputs in `x`. Returns a matrix of size `(length(x), length(x))` satisfying `kernelmatrix(κ, x)[p, q] == κ(x[p], x[q])`.

```
kernelmatrix(κ::Kernel, x::AbstractVector, y::AbstractVector)
```

Compute the kernel `κ` for each pair of inputs in `x` and `y`. Returns a matrix of size `(length(x), length(y))` satisfying `kernelmatrix(κ, x, y)[p, q] == κ(x[p], y[q])`.

```
kernelmatrix(κ::Kernel, X::AbstractMatrix; obsdim)
kernelmatrix(κ::Kernel, X::AbstractMatrix, Y::AbstractMatrix; obsdim)
```

If `obsdim=1`, equivalent to `kernelmatrix(κ, RowVecs(X))` and `kernelmatrix(κ, RowVecs(X), RowVecs(Y))`, respectively. If `obsdim=2`, equivalent to `kernelmatrix(κ, ColVecs(X))` and `kernelmatrix(κ, ColVecs(X), ColVecs(Y))`, respectively.

See also: [`ColVecs`](@ref), [`RowVecs`](@ref)
