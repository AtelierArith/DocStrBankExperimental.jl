```
Rangx, A, B = RangEn(Sig)
```

Returns the range entropy estimate (`Rangx`) and the number of matched state vectors (`m: B`, `m+1: A`) estimated from the data sequence (`Sig`) using the sample entropy algorithm and the following default parameters:  embedding dimension = 2, time delay = 1, radius threshold = 0.2, logarithm = natural.    

```
Rangx, A, B = RangEn(Sig::AbstractArray{T,1} where T<:Real; m::Int=2, tau::Int=1, r::Real=0.2, Methodx::String="SampEn", Logx::Real=exp(1))
```

Returns the range entropy estimates (`Rangx`) for dimensions = `m` estimated for the data sequence (`Sig`) using the specified keyword arguments:

# Arguments:

`m`         - Embedding Dimension, a positive integer

`tau`       - Time Delay, a positive integer

`r`         - Radius Distance Threshold, a positive value between 0 and 1

`Methodx`   - Base entropy method, either 'SampEn' [default] or 'ApEn'

`Logx`      - Logarithm base, a positive scalar  

# See also `ApEn`, `SampEn`, `FuzzEn`,  `MSEn`

# References:

```
[1] Omidvarnia, Amir, et al.
    "Range entropy: A bridge between signal complexity and self-similarity"
    Entropy 
    20.12 (2018): 962.
    
[2] Joshua S Richman and J. Randall Moorman. 
    "Physiological time-series analysis using approximate entropy
    and sample entropy." 
    American Journal of Physiology-Heart and Circulatory Physiology 
    2000
```
