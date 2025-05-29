```
kernelmatrix_diag!(K::AbstractVector, κ::Kernel, x::AbstractVector)
kernelmatrix_diag!(K::AbstractVector, κ::Kernel, x::AbstractVector, y::AbstractVector)
```

[`kernelmatrix_diag`](@ref) のインプレースバージョンです。

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

`obsdim=1` の場合、`kernelmatrix_diag!(K, κ, RowVecs(X))` および `kernelmatrix_diag!(K, κ, RowVecs(X), RowVecs(Y))` に相当します。`obsdim=2` の場合、`kernelmatrix_diag!(K, κ, ColVecs(X))` および `kernelmatrix_diag!(K, κ, ColVecs(X), ColVecs(Y))` に相当します。

関連情報: [`ColVecs`](@ref), [`RowVecs`](@ref)
