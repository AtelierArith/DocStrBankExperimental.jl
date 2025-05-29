```julia
(1)
function decibel(S :: Union{Real, AbstractArray{T}}) where T<:Real

(2)
function decibel(S1 :: Union{Real, AbstractArray{T}},
            S2 :: Union{Real, AbstractArray{T}}) where T<:Real
```

Convert (1) a measure `S`, or (2) a ratio between two measures `S1`./`S2` into deciBels.

Input measures can be real numbers or real arrays of any dimensions.

For array input, the ratio and the conversion is computed element-wise.

**Examples**:

```julia
using FourierAnalysis
v=sinusoidal(3., 1, 128, 256, 0)
s=spectra(v, 128, 256; func=decibel) # compute the spectra in dB
s.y # show the spectra

decibel(s.y)

decibel(10.0)

N=abs.(randn(3, 3))
decibel(N)
```
