```
function slider(vals::AbstractArray;
                value=medianelement(vals),
                label=nothing, readout=true, kwargs...)
```

Creates a slider widget which can take on the values in `vals`, and updates observable `value` when the slider is changed.
