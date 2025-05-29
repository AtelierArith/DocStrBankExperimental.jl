```
UnitaryGroup{T}
```

特別直交群 $\mathrm{U}(n)$ は、行列の積演算 [`MatrixMultiplicationGroupOperation`](@ref) に関するリー群であり、回転の多様体 [`UnitaryMatrices`](@extref `Manifolds.GeneralUnitaryMatrices`) 上で、行列式の絶対値が1であるものです。

# コンストラクタ

```
UnitaryGroup(n::Int, 𝔽::AbstractNumbers=ℂ; kwargs...)
```

ユニタリ群 $\mathrm{U}(n)$ を生成します。`kwargs...` のすべてのキーワード引数は、[`Rotations`](@extref `Manifolds.Rotations`) にも渡されます。
