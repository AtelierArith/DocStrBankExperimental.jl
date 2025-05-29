```
TimeBoundary{N}(upper_bound::Float64, lower_bound::Float64) <: AbstractBoundary{N}
```

静止している観測者が座標系の中心で知覚する適切な時間が `upper_bound` と `lower_bound` の間にある領域。この概念は、コンフォーマルにタイムスライス可能な多様体でコンパクトな時空スライスを持つ場合にのみ意味を持つため、[`HypercylinderManifold`](@ref) と [`DeSitterManifold`](@ref) のみに定義されています。
