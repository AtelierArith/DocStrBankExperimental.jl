```
status(d::D2XXDevice) ->
  mflaglist::Dict{String, Bool}, lflaglist::Dict{String, Bool}
```

Return `Bool` dictionaries of flags for  the modem status (`mflaglist`) and  line status (`lflaglist`) for an open [`D2XXDevice`](@ref) using  [`FT_GetModemStatus`](@ref).
