```julia
mutable struct BivariateKDE{Rx<:AbstractRange, Ry<:AbstractRange} <: KernelDensity.AbstractKDE
```

実数直線上のKDEのために、グリッドと密度の両方を保存します。

フィールドを直接読み取ることはAPIの一部であり、

```julia
sum(density) * step(x) * step(y) ≈ 1
```

# フィールド

  * `x`: 密度を評価するためのグリッドポイントの最初の座標。
  * `y`: 密度を評価するためのグリッドポイントの2番目の座標。
  * `density`: 対応するグリッドポイント `Tuple.(x, permutedims(y))` におけるカーネル密度。
