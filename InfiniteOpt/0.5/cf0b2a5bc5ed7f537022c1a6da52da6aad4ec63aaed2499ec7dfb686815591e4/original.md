```
JuMP.lower_bound(data::AbstractMeasureData)::Union{Float64, Vector{Float64}}
```

Return the lower bound associated with `data` that defines its domain. This is intended as an internal method, but may be useful for extensions. User-defined measure data types should extend this function if desired, otherwise `NaN` is returned
