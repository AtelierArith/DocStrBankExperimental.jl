```
is_stable(report::StabilityReport)::Bool
is_stable(reports::AbstractArray{StabilityReport})::Bool
is_stable(reports::AbstractArray{Tuple{<:Any, StabilityReport}})::Bool
```

Check if the given [`StabilityReport`](@ref)s don't have any unstable types.
