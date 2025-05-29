```
catchments(dir, sinks::Union{Vector{Vector{CartesianIndex{2}}}, Vector{<:CartesianIndices{2}}}, dem=nothing;
                check_sinks_overlap=true)
```

Make a map of catchments from different (non-overlapping) sinks.

See also: `catchment`
