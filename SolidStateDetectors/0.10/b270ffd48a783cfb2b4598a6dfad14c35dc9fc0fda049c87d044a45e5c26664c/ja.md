```
is_depleted(point_types::PointTypes)::Bool
```

すべての [`PointType`](@ref) 値が [`Simulation`](@ref) の [`PointTypes`](@ref) で枯渇としてマークされている場合は `true` を返し、[`PointTypes`](@ref) のいずれかのポイントが未枯渇としてマークされている場合は `false` を返します。

これは、指定されたバイアス電圧で [`SolidStateDetector`](@ref) が枯渇しているかどうかを判断するために使用できます。

## 引数

  * `point_types::PointTypes`: [`Simulation`](@ref) の [`PointTypes`](@ref)。

## 例

```julia
is_depleted(sim.point_types)
```
