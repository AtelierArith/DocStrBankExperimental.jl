```
  XAp, Phi = XApEn(Sig1, Sig2)
```

Returns the cross-approximate entropy estimates (`XAp`) and the average   number of matched vectors (`Phi`) for m = [0,1,2], estimated for the data   sequences contained in `Sig1` and `Sig2` using the default parameters:   embedding dimension = 2, time delay = 1,    radius distance threshold= 0.2*SDpooled(`Sig1`,`Sig2`), logarithm = natural

**NOTE**: XApEn is direction-dependent. Thus, `Sig1` is used as the template data sequence,   and `Sig2` is the matching sequence.``

```
  XAp, Phi = XApEn(Sig1::Union{AbstractMatrix{T}, AbstractVector{T}} where T<:Real, Sig2::Union{AbstractVector{T} where T<:Real, Nothing} = nothing; m::Int=2, tau::Int=1, r::Union{Real,Nothing}=nothing, Logx::Real=exp(1))
```

Returns the cross-approximate entropy estimates (`XAp`) between the data   sequences contained in `Sig1` and `Sig2` using the specified 'keyword' arguments:

# Arguments:

`m`     - Embedding Dimension, a positive integer  [default: 2] 

`tau`   - Time Delay, a positive integer        [default: 1]  

`r`     - Radius Distance Threshold, a positive scalar [default: 0.2*SDpooled(`Sig1`,`Sig2`)] 

`Logx`  - Logarithm base, a positive scalar     [default: natural]  

# See also `XSampEn`, `XFuzzEn`, `XMSEn`, `ApEn`, `SampEn`, `MSEn`

# References:

```
  [1] Steven Pincus and Burton H. Singer,
      "Randomness and degrees of irregularity." 
      Proceedings of the National Academy of Sciences 
      93.5 (1996): 2083-2088.

  [2] Steven Pincus,
      "Assessing serial irregularity and its implications for health."
      Annals of the New York Academy of Sciences 
      954.1 (2001): 245-267.
```
