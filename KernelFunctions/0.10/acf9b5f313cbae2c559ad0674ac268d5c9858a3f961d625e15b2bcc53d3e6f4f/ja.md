```
kernelmatrix_diag(κ::Kernel, x::AbstractVector)
```

`kernelmatrix(κ, x)`の対角成分を効率的に計算します。

```
kernelmatrix_diag(κ::Kernel, x::AbstractVector, y::AbstractVector)
```

`kernelmatrix(κ, x, y)`の対角成分を効率的に計算します。`x`と`y`は同じ長さである必要があります。

```
kernelmatrix_diag(κ::Kernel, X::AbstractMatrix; obsdim)
kernelmatrix_diag(κ::Kernel, X::AbstractMatrix, Y::AbstractMatrix; obsdim)
```

`obsdim=1`の場合、`kernelmatrix_diag(κ, RowVecs(X))`および`kernelmatrix_diag(κ, RowVecs(X), RowVecs(Y))`に相当します。`obsdim=2`の場合、`kernelmatrix_diag(κ, ColVecs(X))`および`kernelmatrix_diag(κ, ColVecs(X), ColVecs(Y))`に相当します。

参照: [`ColVecs`](@ref), [`RowVecs`](@ref)
