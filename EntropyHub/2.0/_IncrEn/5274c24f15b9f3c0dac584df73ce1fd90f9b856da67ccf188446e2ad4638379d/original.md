```
Incr = IncrEn(Sig)
```

Returns the increment entropy (`Incr`) estimate of the data sequence  (`Sig`) using the default parameters:  embedding dimension = 2, time delay = 1, quantifying resolution = 4, logarithm = base 2,

```
Incr = IncrEn(Sig::AbstractArray{T,1} where T<:Real; m::Int=2, tau::Int=1, R::Int=4, Logx::Real=2, Norm::Bool=false)
```

Returns the increment entropy (`Incr`) estimate of the data sequence (`Sig`) using the specified 'keyword' arguments:

# Arguments:

`m`     - Embedding Dimension, an integer > 1   

`tau`   - Time Delay, a positive integer    

`R`     - Quantifying resolution, a positive scalar    

`Logx`  - Logarithm base, a positive scalar (enter 0 for natural log) 

`Norm`  - Normalisation of IncrEn value: 

```
      [false]  no normalisation - default
      [true]   normalises w.r.t embedding dimension (m-1).
```

# See also `PermEn`, `SyDyEn`, `MSEn`

# References:

```
[1] Xiaofeng Liu, et al.,
    "Increment entropy as a measure of complexity for time series."
    Entropy
    18.1 (2016): 22.1.

***   "Correction on Liu, X.; Jiang, A.; Xu, N.; Xue, J. - Increment 
    Entropy as a Measure of Complexity for Time Series,
    Entropy 2016, 18, 22." 
    Entropy 
    18.4 (2016): 133.

[2] Xiaofeng Liu, et al.,
    "Appropriate use of the increment entropy for 
    electrophysiological time series." 
    Computers in biology and medicine 
    95 (2018): 13-23.
```
