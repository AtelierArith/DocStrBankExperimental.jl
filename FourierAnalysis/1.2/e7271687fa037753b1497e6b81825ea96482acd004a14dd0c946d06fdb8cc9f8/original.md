```julia
function b2f(bin :: Int,
              sr :: Int,
              wl :: Int;
        DC :: Bool = false)
```

**b**in **to f**requency. Return the closest discrete Fourier frequency (in Hz) that corresponds to a bin (position) in a real-FFT vector, given sampling rate `sr` and window length `wl`. The FFT vector is assumed to be 1-based, as always in Julia.

If `DC` is false, the first discrete frequency is assumed to be at bin 1, otherwise the DC level is assumed to be at bin 1 and the first discrete frequency at bin 2.

**See also**: [`f2b`](@ref), [`fres`](@ref), [`fdf`](@ref), [`brange`](@ref).

**Examples**:

```julia
using FourierAnalysis
f2b(20, 512, 1024) # return 40
f2b(10, 128, 128) # return 10
```
