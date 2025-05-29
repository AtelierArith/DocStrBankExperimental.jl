```julia
function fdf(sr :: Int,
             wl :: Int;
          DC :: Bool = false)
```

Return a vector with all **F**ourier **d**iscrete **f**requencies for a real-FFT, given sampling rate `sr` and window length `wl`. If `DC` is false, the first discrete frequency starts at bin (position) 1 and the length of the vector is $wl÷2$ (integer division), otherwise the DC level is at position 1. and the length of the vector is $(wl÷2)+1$.

**See also**: [`f2b`](@ref), [`fres`](@ref), [`b2f`](@ref), [`brange`](@ref).

**Examples**:

```julia
using FourierAnalysis
fdf(8, 16)
# return the 8-element Array{Float64,1}:
# [0.5, 1.0, 1.5, 2.0, 2.5, 3, 3.5, 4.0]
```
