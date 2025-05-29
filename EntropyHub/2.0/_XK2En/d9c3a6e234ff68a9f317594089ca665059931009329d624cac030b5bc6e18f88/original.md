```
XK2, Ci = XK2En(Sig1, Sig2)
```

Returns the cross-Kolmogorov entropy estimates (`XK2`) and the correlation integrals (`Ci`) for m = [1,2] estimated between the data sequences  contained in `Sig1` and `Sig2` using the default parameters:  embedding dimension = 2, time delay = 1, distance threshold (r) = 0.2*SDpooled(Sig1, Sig2), logarithm = natural

```
XK2, Ci = XK2En(Sig1::Union{AbstractMatrix{T}, AbstractVector{T}} where T<:Real, Sig2::Union{AbstractVector{T} where T<:Real, Nothing} = nothing; m::Int=2, tau::Int=1, r::Union{Real,Nothing}=nothing, Logx::Real=exp(1))
```

Returns the cross-Kolmogorov entropy estimates (`XK2`) estimated between the data sequences contained in `Sig1` and `Sig2` using the specified 'keyword' arguments:

# Arguments:

`m`     - Embedding Dimension, a positive integer [default: 2]  

`tau`   - Time Delay, a positive integer         [default: 1]  

`r`     - Radius Distance Threshold, a positive scalar  [default: 0.2*SDpooled(`Sig1`,`Sig2`)]  

`Logx`  - Logarithm base, a positive scalar      [default: natural]  

# See also `XSampEn`, `XFuzzEn`, `XApEn`, `K2En`, `XMSEn`, `XDistEn`

# References:

```
[1]  Matthew W. Flood,
     "XK2En - EntropyHub Project"
     (2021) https://github.com/MattWillFlood/EntropyHub
```
