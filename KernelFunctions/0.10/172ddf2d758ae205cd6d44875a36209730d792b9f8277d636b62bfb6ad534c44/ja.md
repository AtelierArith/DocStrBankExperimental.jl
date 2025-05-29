```
kernelmatrix!(K::AbstractMatrix, κ::Kernel, x::AbstractVector)
kernelmatrix!(K::AbstractMatrix, κ::Kernel, x::AbstractVector, y::AbstractVector)
```

事前に割り当てられた行列 `K` がカーネル行列で上書きされる [`kernelmatrix`](@ref) のインプレースバージョンです。

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

`obsdim=1` の場合、`kernelmatrix!(K, κ, RowVecs(X))` および `kernelmatrix(K, κ, RowVecs(X), RowVecs(Y))` に相当します。`obsdim=2` の場合、`kernelmatrix!(K, κ, ColVecs(X))` および `kernelmatrix(K, κ, ColVecs(X), ColVecs(Y))` に相当します。

関連情報: [`ColVecs`](@ref), [`RowVecs`](@ref)
