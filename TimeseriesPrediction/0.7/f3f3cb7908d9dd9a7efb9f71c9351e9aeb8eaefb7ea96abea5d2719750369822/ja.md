```
ConstantBoundary(b) <: AbstractBoundaryCondition
```

定常境界条件タイプ。再構成時に境界外の欠損値をパラメータ `b` で埋めることによって、[`SpatioTemporalEmbedding`](@ref) に渡されたときに定常境界条件を強制します。
