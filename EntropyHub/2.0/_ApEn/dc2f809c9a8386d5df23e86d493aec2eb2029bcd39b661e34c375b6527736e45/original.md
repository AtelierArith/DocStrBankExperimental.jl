```
  Ap, Phi = ApEn(Sig)
```

Returns the approximate entropy estimates `Ap` and the log-average number of    matched vectors `Phi` for `m` = [0,1,2], estimated from the data sequence `Sig`   using the default parameters: embedding dimension = 2, time delay = 1,   radius distance threshold = 0.2*SD(`Sig`), logarithm = natural

```
  Ap, Phi = ApEn(Sig::AbstractArray{T,1} where T<:Real; m::Int=2, tau::Int=1, r::Real=0.2*std(Sig,corrected=false), Logx::Real=exp(1))
```

Returns the approximate entropy estimates `Ap` of the data sequence `Sig`   for dimensions = [0,1,...,`m`] using the specified keyword arguments:

# Arguments:

`m`      - Embedding Dimension, a positive integer

`tau`    - Time Delay, a positive integer

`r`      - Radius Distance Threshold, a positive scalar  

`Logx`   - Logarithm base, a positive scalar

# See also `XApEn`, `SampEn`, `MSEn`, `FuzzEn`, `PermEn`, `CondEn`, `DispEn`

# References:

```
  [1] Steven M. Pincus, 
      "Approximate entropy as a measure of system complexity." 
      Proceedings of the National Academy of Sciences 
      88.6 (1991): 2297-2301.
```
