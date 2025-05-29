```
XSamp, A, B = XSampEn(Sig1, Sig2)
```

Returns the cross-sample entropy estimates (`XSamp`) and the number of  matched vectors (m:B, m+1:A) for m = [0,1,2] estimated for the two  univariate data sequences contained in `Sig1` and  `Sig2` using the default parameters: embedding dimension = 2, time delay = 1,  radius distance threshold= 0.2*SDpooled(`Sig1`,`Sig2`),  logarithm = natural

```
XSamp, A, B, (Vcp, Ka, Kb) = XSampEn(Sig1, Sig2, ..., Vcp = true)
```

If `Vcp == true`, an additional tuple `(Vcp, Ka, Kb)` is returned with     the cross-sample entropy estimates (`XSamp`) and the number of matched state vectors (`m: B`, `m+1: A`). `(Vcp, Ka, Kb)` contains the variance of the conditional probabilities (`Vcp`), i.e. CP = A/B,  and the number of **overlapping** matching vector pairs of lengths m+1 (`Ka`) and m (`Kb`), respectively.  Note `Vcp` is undefined for the zeroth embedding dimension (m = 0)  and due to the computational demand, **will take substantially more time to return function outputs.** See Appendix B in [2] for more info.

```
XSamp, A, B = XSampEn(Sig1::Union{AbstractMatrix{T}, AbstractVector{T}} where T<:Real, Sig2::Union{AbstractVector{T} where T<:Real, Nothing} = nothing; m::Int=2, tau::Int=1, r::Union{Real,Nothing}=nothing, Logx::Real=exp(1), Vcp::Bool=false)
```

Returns the cross-sample entropy estimates (`XSamp`) for dimensions [0,1,...,m] estimated between the data sequences in `Sig1` and `Sig2` using the specified  'keyword'  arguments:

# Arguments:

`m`     - Embedding Dimension, a positive integer  [default: 2]   

`tau`   - Time Delay, a positive integer         [default: 1]   

`r`     - Radius Distance Threshold, a positive scalar [default: 0.2*SDpooled(`Sig1`,`Sig2`)] 

`Logx`  - Logarithm base, a positive scalar      [default: natural] 

`Vcp`   - Option to return the variance of the conditional probabilities and the number of overlapping matching vector pairs of lengths 

See also `XFuzzEn`, `XApEn`, `SampEn`, `SampEn2D`, `XMSEn`, `ApEn`

# References:

```
[1] Joshua S Richman and J. Randall Moorman. 
    "Physiological time-series analysis using approximate entropy
    and sample entropy." 
    American Journal of Physiology-Heart and Circulatory Physiology
    (2000)

[2] Douglas E Lake, Joshua S Richman, M.P. Griffin, J. Randall Moorman
    "Sample entropy analysis of neonatal heart rate variability."
    American Journal of Physiology-Regulatory, Integrative and Comparative Physiology
    283, no. 3 (2002): R789-R797.
```
