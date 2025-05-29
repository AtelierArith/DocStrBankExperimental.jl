```
function rangepicker(vals::AbstractArray;
                value=[extrema(vals)...],
                label=nothing, readout=true, kwargs...)
```

A multihandle slider with a set of spinboxes, one per handle.
