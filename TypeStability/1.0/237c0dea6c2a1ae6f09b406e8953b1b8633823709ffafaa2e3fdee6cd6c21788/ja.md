```
is_stable(report::StabilityReport)::Bool
is_stable(reports::AbstractArray{StabilityReport})::Bool
is_stable(reports::AbstractArray{Tuple{<:Any, StabilityReport}})::Bool
```

与えられた [`StabilityReport`](@ref) が不安定な型を持たないか確認します。
