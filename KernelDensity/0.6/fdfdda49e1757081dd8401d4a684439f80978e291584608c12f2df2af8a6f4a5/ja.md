```julia
mutable struct UnivariateKDE{R<:AbstractRange} <: KernelDensity.AbstractKDE
```

$$
ℝ²
$$

上のKDEのためのグリッドと密度の両方を保存します。

フィールドを直接読み取ることはAPIの一部であり、

```julia
sum(density) * step(x) ≈ 1
```

# フィールド

  * `x`: 密度を評価するためのグリッドポイント。
  * `density`: 対応するグリッドポイント `x` でのカーネル密度。
