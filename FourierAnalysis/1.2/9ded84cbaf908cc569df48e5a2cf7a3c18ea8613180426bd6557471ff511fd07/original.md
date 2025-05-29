```julia
function goertzel( x   :: AbstractVector{T},
                   f   :: IntOrReal,
                   sr  :: Int,
                   wl  :: Int,
               startAT :: Int = 1) where T<:Union{Real, Complex}
```

Given a time series as input vector `x` sampled at `sr` sampling rate, return the DFT complex coefficient at the discrete Fourier frequency which is the closest to `f`. The coefficient is computed for the time window starting at `startAt` (one-based) and of lenght `wl`.

If `startAT`=1 (default) the first `wl` samples of the vector are considered.

`wl` does not need to be power of 2.

**See also**: [`goertzel_fast`](@ref), [`goertzel2`](@ref).

**Examples**:

```julia
using FourierAnalysis
sr, t, f, a = 128, 128, 5, 10
v=sinusoidal(a, f, sr, t, 0)
c=goertzel(v, f, sr, t) # should output 0+aim
```
