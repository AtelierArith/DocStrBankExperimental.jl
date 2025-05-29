```
NWState(nw_or_nw_wrapper;
        utype=Vector{Float64}, ufill=filltype(utype),
        ptype=Vector{Float64}, pfill=filltype(ptype), default=true)
```

Creates "empty" `NWState` object for the Network/Wrapper `nw` with flat types `utype` & `ptype`. The arrays will be prefilled with `ufill` and `pfill` respectively (defaults to NaN).

If `default=true` the default state & parameter values attached to the network components will be loaded.
