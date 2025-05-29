```
OrthogonalGroup{T}
```

直交群 $\mathrm{O}(n)$ は、回転の多様体 [`OrthogonalMatrices`](@extref `Manifolds.OrthogonalMatrices`) 上の [`MatrixMultiplicationGroupOperation`](@ref) からなるリー群です。

# コンストラクタ

```
OrthogonalGroup(n::Int; kwargs...)
```

直交群 $\mathrm{O}(n)$ を生成します。`kwargs...` のすべてのキーワード引数は、[`OrthogonalMatrices`](@extref `Manifolds.OrthogonalMatrices`) にも渡されます。
