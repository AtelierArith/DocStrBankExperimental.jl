```
kernelmatrix(κ::Kernel, x::AbstractVector)
```

入力 `x` の各ペアに対してカーネル `κ` を計算します。サイズ `(length(x), length(x))` の行列を返し、`kernelmatrix(κ, x)[p, q] == κ(x[p], x[q])` を満たします。

```
kernelmatrix(κ::Kernel, x::AbstractVector, y::AbstractVector)
```

入力 `x` と `y` の各ペアに対してカーネル `κ` を計算します。サイズ `(length(x), length(y))` の行列を返し、`kernelmatrix(κ, x, y)[p, q] == κ(x[p], y[q])` を満たします。

```
kernelmatrix(κ::Kernel, X::AbstractMatrix; obsdim)
kernelmatrix(κ::Kernel, X::AbstractMatrix, Y::AbstractMatrix; obsdim)
```

`obsdim=1` の場合、`kernelmatrix(κ, RowVecs(X))` および `kernelmatrix(κ, RowVecs(X), RowVecs(Y))` に相当します。`obsdim=2` の場合、`kernelmatrix(κ, ColVecs(X))` および `kernelmatrix(κ, ColVecs(X), ColVecs(Y))` に相当します。

参照: [`ColVecs`](@ref), [`RowVecs`](@ref)
