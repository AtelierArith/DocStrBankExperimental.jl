```
readPolarizedMapFromFITS{T}(fileName::AbstractString, column, t::Type{T})
```

Read a polarized map (I/Q/U) from a FITS file and return a [`PolarizedHealpixMap`](@ref) object.

The parameter `column` can be either a number or a 3-element tuple. In the first case, three consecutive columns will be read starting from `column` (1-based index), otherwise the three column indices will be used.
