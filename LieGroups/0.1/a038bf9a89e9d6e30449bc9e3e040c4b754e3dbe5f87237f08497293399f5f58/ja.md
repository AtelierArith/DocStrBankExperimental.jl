```
SpecialOrthogonalGroup{T}
```

特別直交群 $\mathrm{SO}(n)$ は、回転の多様体 [`Rotations`](@extref `Manifolds.Rotations`) 上の [`MatrixMultiplicationGroupOperation`](@ref) からなるリー群です。

# コンストラクタ

```
SpecialOrthogonalGroup(n::Int; kwargs...)
```

特別直交群 $\mathrm{SO}(n)$ を生成します。`kwargs...` のすべてのキーワード引数は、[`Rotations`](@extref `Manifolds.Rotations`) にも渡されます。
