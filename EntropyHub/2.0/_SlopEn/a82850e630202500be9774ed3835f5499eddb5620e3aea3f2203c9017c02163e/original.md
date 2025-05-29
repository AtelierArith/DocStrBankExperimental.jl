```
Slop = SlopEn(Sig)
```

Returns the slope entropy (`Slop`) estimates for embedding dimensions [2, ..., m] of the data sequence (`Sig`) using the default parameters: embedding dimension = 2, time delay = 1,  angular thresholds = [5 45],  logarithm = base 2 

```
Slop = SlopEn(Sig::AbstractArray{T,1} where T<:Real; m::Int=2, tau::Int=1, Lvls::AbstractArray{T,1} where T<:Real=[5, 45], Logx::Real=2, Norm::Bool=true)
```

Returns the slope entropy (`Slop`) estimate of the data sequence (`Sig`)   using the specified 'keyword' arguments:

# Arguments:

`m`     - Embedding Dimension, an integer > 1   	

```
      SlopEn returns estimates for each dimension [2,...,m]
```

`tau`   - Time Delay, a positive integer    

`Lvls`  - Angular thresolds, a vector of monotonically increasing              values in the range [0 90] degrees.

`Logx`  - Logarithm base, a positive scalar (enter 0 for natural log)   

`Norm`  - Normalisation of SlopEn value, a boolean operator: 

```
      [false]  no normalisation
      [true]   normalises w.r.t. the number of patterns found (default)
```

# See also `PhasEn`, `GridEn`, `MSEn`, `CoSiEn`, `SampEn`, `ApEn`

# References:

```
[1] David Cuesta-Frau,
    "Slope Entropy: A New Time Series Complexity Estimator Based on
    Both Symbolic Patterns and Amplitude Information." 
    Entropy 
    21.12 (2019): 1167.
```
