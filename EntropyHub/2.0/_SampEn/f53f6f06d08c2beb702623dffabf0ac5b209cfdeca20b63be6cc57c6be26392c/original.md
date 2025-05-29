```
Samp, A, B = SampEn(Sig)
```

Returns the sample entropy estimates `Samp` and the number of matched state   vectors (`m`:B, `m+1`:A) for `m` = [0,1,2] estimated from the data sequence `Sig`  using the default parameters: embedding dimension = 2, time delay = 1,   radius threshold = 0.2*SD(`Sig`), logarithm = natural

```
Samp, A, B, (Vcp, Ka, Kb) = SampEn(Sig, ..., Vcp = true)
```

If `Vcp == true`, an additional tuple `(Vcp, Ka, Kb)` is returned with      the sample entropy estimates (`Samp`) and the number of matched state  vectors (`m: B`, `m+1: A`). `(Vcp, Ka, Kb)`  contains the variance of the conditional  probabilities (`Vcp`), i.e. CP = A/B,  and the number of **overlapping**  matching vector pairs of lengths m+1 (`Ka`) and m (`Kb`),  respectively.  Note `Vcp` is undefined for the zeroth embedding dimension (m = 0)   and due to the computational demand, **will take substantially more time to return function outputs.**  See Appendix B in [2] for more info.

```
Samp, A, B = SampEn(Sig::AbstractArray{T,1} where T<:Real; m::Int=2, tau::Int=1, r::Real=0.2*std(Sig,corrected=false), Logx::Real=exp(1), Vcp::Bool=false)
```

Returns the sample entropy estimates `Samp` for dimensions = [0,1,...,`m`]  estimated from the data sequence `Sig` using the specified keyword arguments:

# Arguments:

`m`     - Embedding Dimension, a positive integer

`tau`   - Time Delay, a positive integer

`r`     - Radius Distance Threshold, a positive scalar  

`Logx`  - Logarithm base, a positive scalar 

`Vcp`   - Option to return the variance of the conditional probabilities and the number of overlapping matching vector pairs of lengths 

# See also `ApEn`, `FuzzEn`, `PermEn`, `CondEn`, `XSampEn`, `SampEn2D`, `MSEn`

# References:

```
[1] Joshua S Richman and J. Randall Moorman. 
    "Physiological time-series analysis using approximate entropy
    and sample entropy." 
    American Journal of Physiology-Heart and Circulatory Physiology (2000).

[2] Douglas E Lake, Joshua S Richman, M.P. Griffin, J. Randall Moorman
    "Sample entropy analysis of neonatal heart rate variability."
    American Journal of Physiology-Regulatory, Integrative and Comparative Physiology
    283, no. 3 (2002): R789-R797.
```
