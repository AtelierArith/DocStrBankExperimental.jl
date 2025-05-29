```
rescale!(x::AbstractArray;
    interval=nothing, calibration=nothing, window=nothing)
```

Rescale array x to the interval specified by `interval`.

If `calibration` is not `nothing`, then rescaling is done with reference to the values given by `calibration`. In other words, minimum and maximum are assumed to be the values specified by `calibration`.

See also: [`rescale`](@ref)
