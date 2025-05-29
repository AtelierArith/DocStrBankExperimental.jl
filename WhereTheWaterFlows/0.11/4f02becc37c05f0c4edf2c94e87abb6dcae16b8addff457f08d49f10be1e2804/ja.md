```
catchments(dir, sinks::Union{Vector{Vector{CartesianIndex{2}}}, Vector{<:CartesianIndices{2}}}, dem=nothing;
                check_sinks_overlap=true)
```

異なる（重ならない）シンクからの集水域の地図を作成します。

参照: `catchment`
