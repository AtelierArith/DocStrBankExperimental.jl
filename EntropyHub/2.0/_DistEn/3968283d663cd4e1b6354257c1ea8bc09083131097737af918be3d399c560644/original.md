```
Dist, Ppi = DistEn(Sig)
```

Returns the distribution entropy estimate (`Dist`) and the corresponding distribution probabilities (`Ppi`) estimated from  the data sequence (`Sig`) using the default  parameters:  embedding dimension = 2, time delay = 1, binning method = 'Sturges', logarithm = base 2, normalisation = w.r.t # of histogram bins

```
Dist, Ppi = DistEn(Sig::AbstractArray{T,1} where T<:Real; m::Int=2, tau::Int=1, Bins::Union{Int,String}="Sturges", Logx::Real=2, Norm::Bool=true)
```

Returns the distribution entropy estimate (`Dist`) estimated from  the data sequence (`Sig`) using the specified 'keyword' arguments:

# Arguments:

`m`     - Embedding Dimension, a positive integer  

`tau`   - Time Delay, a positive integer  

`Bins`  - Histogram bin selection method for distance distribution,            one of the following:  

```
      an integer > 1 indicating the number of bins, or one of the 
      following strings {'sturges','sqrt','rice','doanes'}
      [default: 'sturges']
```

`Logx`  - Logarithm base, a positive scalar (enter 0 for natural log)   

`Norm`  - Normalisation of DistEn value:  

```
      [false]  no normalisation.
      [true]   normalises w.r.t # of histogram bins - default
```

# See also `XDistEn`, `DistEn2D`, `MSEn`, `K2En`

# References:

```
[1] Li, Peng, et al.,
    "Assessing the complexity of short-term heartbeat interval 
    series by distribution entropy." 
    Medical & biological engineering & computing 
    53.1 (2015): 77-87.
```
