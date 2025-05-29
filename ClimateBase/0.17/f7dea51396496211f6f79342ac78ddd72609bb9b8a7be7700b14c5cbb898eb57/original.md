```
realtime_milliseconds(t::AbstractArray{<:TimeType}, T = Float64)
```

Similar with [`realtime_days`](@ref), but now the measurement unit is millisecond. For extra accuracy, direct differences in `t` are used.
