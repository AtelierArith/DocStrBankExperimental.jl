```
FQList(values, unit::Symbol, relative::Bool)
```

Represents a frequency list. `unit` can be `:Hz` or `:ppm`, and `relative` indicates whether the frequency is given relative to SFO (true) or BF (false).

Raw values can be extracted using the `data` function, or (better) as absolute chemical shifts (in ppm) or relative offsets (in Hz) using [`getppm`](@ref) and [`getoffset`](@ref) functions.

See also: [`getppm`](@ref), [`getoffset`](@ref).
