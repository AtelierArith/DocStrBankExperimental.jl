```
NWParameter(nw_or_nw_wraper;
            ptype=Vector{Float64}, pfill=filltype(ptype), default=true)
```

Creates "empty" `NWParameter` object for the Network/Wrapper `nw` with flat type `ptype`. The array will be prefilled with `pfill` (defaults to NaN).

If `default=true` the default parameter values attached to the network components will be loaded.
