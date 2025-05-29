```julia
function fres(sr :: Int,
              wl :: Int)
```

FFT **f**requency **res**olution given sampling rate `sr` and window length `wl`.

**See also**: [`f2b`](@ref), [`b2f`](@ref), [`fdf`](@ref), [`brange`](@ref).

**Examples**:

```julia
using FourierAnalysis
fres(1024, 2048) # return 0.5
```
