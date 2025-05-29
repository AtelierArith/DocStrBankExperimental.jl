```julia
function f2b(f :: IntOrReal,
            sr :: Int,
            wl :: Int;
        DC :: Bool = false)
```

**f**requency **to b**in. Return the bin (position) in a real-FFT vector best matching a frequency `f` (in Hz), given sampling rate `sr` and window length `wl`. The frequency can be given either as an integer or as a real number.

If the requested `f` is exactly in between two Fourier discrete frequencies, then the smallest of the two equidistant frequencies is returned.

The FFT vector is assumed to be 1-based (as always in Julia). If `DC` is false, the first discrete frequency is assumed to be at bin 1, otherwise the DC is assumed to be at bin 1 and the first discrete frequency at bin 2.

If `DC` is false return 0 for frequencies inferior to half the frequency resolution.

**See also**: [`fres`](@ref), [`b2f`](@ref), [`fdf`](@ref), [`brange`](@ref).

**Examples**:

```julia
using FourierAnalysis
f2b(10, 512, 1024) # return 20
```
