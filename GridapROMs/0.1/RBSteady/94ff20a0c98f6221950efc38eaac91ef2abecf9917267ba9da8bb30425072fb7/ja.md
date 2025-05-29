```
abstract type ReducedProjection{A<:AbstractArray} <: Projection end
```

別の `Projection` によって表される縮小部分空間への [`Projection`](@ref) のガレルキン射影を表す型。

サブタイプ:

  * [`ReducedAlgebraicProjection`](@ref)
