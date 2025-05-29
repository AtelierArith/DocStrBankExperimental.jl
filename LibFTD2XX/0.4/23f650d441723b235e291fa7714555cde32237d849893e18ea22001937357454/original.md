```
status(d::D2XXDevice) ->
  mflaglist::Dict{String, Bool}, lflaglist::Dict{String, Bool}
```

Return `Bool` dictionaries of flags for  the modem status (`mflaglist`) and  line status (`lflaglist`) for an open [`FT_HANDLE`](@ref) using  [`FT_GetModemStatus`](@ref).

See also: [`isopen`](@ref), [`open`](@ref)
