```
SpecialUnitaryGroup{T}
```

特別直交群 $\mathrm{SU}(n)$ は、行列の積群演算 [`MatrixMultiplicationGroupOperation`](@ref) に基づく回転の多様体 [`GeneralUnitaryMatrices`](@extref `Manifolds.GeneralUnitaryMatrices`) 上のリー群であり、行列式が1である。

# コンストラクタ

```
SpecialUnitaryGroup(n::Int; kwargs...)
```

特別ユニタリ群 $\mathrm{SU}(n)$ を生成します。`kwargs...` のすべてのキーワード引数は、[`Rotations`](@extref `Manifolds.Rotations`) にも渡されます。
