```
   CoSi, Bm = CoSiEn(Sig)
```

Returns the cosine similarity entropy (`CoSi`) and the corresponding    global probabilities estimated from the data sequence (`Sig`) using the    default parameters:   embedding dimension = 2, time delay = 1,     angular threshold = .1,  logarithm = base 2,

```
   CoSi, Bm = CoSiEn(Sig::AbstractArray{T,1} where T<:Real; m::Int=2, tau::Int=1, r::Real=.1, Logx::Real=2, Norm::Int=0)
```

Returns the cosine similarity entropy (`CoSi`) estimated from the data    sequence (`Sig`) using the specified 'keyword' arguments:

# Arguments:

`m`     - Embedding Dimension, an integer > 1   

`tau`   - Time Delay, a positive integer    

`r`     - Angular threshold, a value in range [0 < r < 1]   

`Logx`  - Logarithm base, a positive scalar (enter 0 for natural log) 

`Norm`  - Normalisation of `Sig`, one of the following integers:    

```
       [0]  no normalisation - default
       [1]  normalises `Sig` by removing median(`Sig`)
       [2]  normalises `Sig` by removing mean(`Sig`)
       [3]  normalises `Sig` w.r.t. SD(`Sig`)
       [4]  normalises `Sig` values to range [-1 1]
```

# See also `PhasEn`, `SlopEn`, `GridEn`, `MSEn`, `cMSEn`

# References:

```
   [1] Theerasak Chanwimalueang and Danilo Mandic,
       "Cosine similarity entropy: Self-correlation-based complexity
       analysis of dynamical systems."
       Entropy 
       19.12 (2017): 652.
```
