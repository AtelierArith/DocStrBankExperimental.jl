```
 get_timeseries(files::AbstractArray, loc; tstep = 1.0)
```

Extract plasma moments and EM field from PIC output `files` at `loc` with nearest neighbor. Currently only works for 2D outputs. If a single point variable is needed, see [`interp1d`](@ref).
