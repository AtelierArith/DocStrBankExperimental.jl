```julia
function bbands(sr :: Int,
                wl :: Int,
         bandwidth :: IntOrReal;
    DC :: Bool = false)
```

Return a vector of integers holding the limits of all `bandwidth`-spaced band-pass regions of a real-FFT, in bins of discrete Fourier frequencies, from one to $wl÷2$ (integer division).

This is used by function [`bands`](@ref).

To know the frequencies in Hz to which these bins correspond, call [`fbands`](@ref).

**See**: [`bands`](@ref).

**See also**: [`fbands`](@ref).

**Examples**:

```julia
using FourierAnalysis
bbands(128, 256, 16) # return [1, 32, 64, 96, 128]
fbands(128, 256, 16) # return [0.5, 16.0, 32.0, 48.0, 64.0]

bbands(128, 256, 16; DC=true) # return [2, 33, 65, 97, 129]
fbands(128, 256, 16; DC=true) # return [0.5, 16.0, 32.0, 48.0, 64.0]

bbands(128, 128, 16) # return [1, 16, 32, 48, 64]
fbands(128, 128, 16) # return [1.0, 16.0, 32.0, 48.0, 64.0]
```
