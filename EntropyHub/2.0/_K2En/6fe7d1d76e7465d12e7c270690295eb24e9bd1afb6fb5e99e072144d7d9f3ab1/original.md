```
K2, Ci = K2En(Sig)
```

Returns the Kolmogorov entropy estimates `K2` and the correlation integrals `Ci` for `m` = [1,2] estimated from the data sequence `Sig` using the default parameters: embedding dimension = 2, time delay = 1,  r = 0.2*SD(`Sig`), logarithm = natural

```
K2, Ci = K2En(Sig::AbstractArray{T,1} where T<:Real; m::Int=2, tau::Int=1, r::Real=0.2*std(Sig,corrected=false), Logx::Real=exp(1))
```

Returns the Kolmogorov entropy estimates `K2` for dimensions = [1,...,`m`] estimated from the data sequence `Sig` using the 'keyword' arguments:

# Arguments:

`m`     - Embedding Dimension, a positive integer

`tau`   - Time Delay, a positive integer

`r`     - Radius, a positive scalar 

`Logx`  - Logarithm base, a positive scalar

# See also `DistEn`, `XK2En`, `MSEn`

# References:

```
[1] Peter Grassberger and Itamar Procaccia,
    "Estimation of the Kolmogorov entropy from a chaotic signal." 
    Physical review A 28.4 (1983): 2591.

[2] Lin Gao, Jue Wang  and Longwei Chen
    "Event-related desynchronization and synchronization 
    quantification in motor-related EEG by Kolmogorov entropy"
    J Neural Eng. 2013 Jun;10(3):03602
```
