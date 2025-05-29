```julia
function goertzel2( x  :: AbstractVector{T},
                    f  :: IntOrReal,
                    sr :: Int,
                    wl :: Int,
                startAT:: Int = 1) where T<:Union{Real, Complex}
```

Like the [`goertzel`](@ref) function, but allows estimating the DFT coefficient in the whole positive real line up to the Nyquist frequency. This is useful when the DFT coefficient is sought for a frequency which is not a discrete Fourier Frequency.

Using an appropriate taper this function allows almost exact recovery of both amplitude and phase at all frequencies in case of one sinusoid, whereas the `goertzel` function can do so only at exact Fourier discrete frequencies.

**See also**: [`goertzel_fast`](@ref), [`goertzel`](@ref).

**Examples**:

```julia
using FourierAnalysis
sr, t, f, a = 128, 128, 5, 10
ftrue=f+0.15
v=sinusoidal(a, ftrue, sr, t, 0 )
c=goertzel(v, f, sr, t) # should be 0+aim, but clearly fails
d=goertzel2(v, ftrue, sr, t) # this get closer
```
