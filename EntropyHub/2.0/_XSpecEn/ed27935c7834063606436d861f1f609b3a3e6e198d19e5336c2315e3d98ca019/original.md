```
   XSpec, BandEn = XSpecEn(Sig)
```

Returns the cross-spectral entropy estimate (`XSpec`) of the full cross-    spectrum and the within-band entropy (`BandEn`) estimated between the data     sequences contained in `Sig` using the default  parameters:     N-point FFT = 2 * max(length(`Sig1`/`Sig2`)) + 1, normalised band edge frequencies = [0 1],    logarithm = base 2, normalisation = w.r.t # of spectrum/band frequency     values.

```
   XSpec, BandEn = XSpecEn(Sig1::Union{AbstractMatrix{T}, AbstractVector{T}} where T<:Real, Sig2::Union{AbstractVector{T} where T<:Real, Nothing} = nothing;  N::Union{Nothing,Int}=nothing, Freqs::Tuple{Real,Real}=(0,1), Logx::Real=exp(1), Norm::Bool=true)
```

Returns the cross-spectral entropy (`XSpec`) and the within-band entropy     (`BandEn`) estimate between the data sequences contained in `Sig1` and `Sig2` using the    following specified 'keyword' arguments:

# Arguments:

`N`     - Resolution of spectrum (N-point FFT), an integer > 1    

`Freqs` - Normalised band edge frequencies, a scalar in range [0 1]              where 1 corresponds to the Nyquist frequency (Fs/2).              **Note: When no band frequencies are entered, BandEn == SpecEn** 

`Logx`  - Logarithm base, a positive scalar     [default: base 2]              ** enter 0 for natural log**  

`Norm`  - Normalisation of `XSpec` value:              [false]  no normalisation.              [true]   normalises w.r.t # of spectrum/band frequency values [default] 

For more info, see the EntropyHub guide

# See also `SpecEn`, `fft`, `XDistEn`, `periodogram`, `XSampEn`, `XApEn`

# References:

```
   [1]  Matthew W. Flood,
       "XSpecEn - EntropyHub Project"
       (2021) https://github.com/MattWillFlood/EntropyHub
```
