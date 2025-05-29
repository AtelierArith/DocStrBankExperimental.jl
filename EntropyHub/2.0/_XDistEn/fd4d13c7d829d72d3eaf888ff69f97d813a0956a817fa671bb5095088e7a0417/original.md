```
  XDist, Ppi = XDistEn(Sig1, Sig2)
```

Returns the cross-distribution entropy estimate (`XDist`) and the   corresponding distribution probabilities (`Ppi`) estimated between the data    sequences contained in `Sig1` and `Sig2` using the default parameters:    embedding dimension = 2, time delay = 1, binning method = 'Sturges',   logarithm = base 2, normalisation = w.r.t # of histogram bins

```
  XDist, Ppi = XDistEn(Sig1::Union{AbstractMatrix{T}, AbstractVector{T}} where T<:Real, Sig2::Union{AbstractVector{T} where T<:Real, Nothing} = nothing; m::Int=2, tau::Int=1, Bins::Union{Int,String}="Sturges", Logx::Real=2, Norm::Bool=true)
```

Returns the cross-distribution entropy estimate (`XDist`) estimated between the    data sequences contained in `Sig1` and `Sig2` using the specified 'keyword' = arguments:

# Arguments:

`m`     - Embedding Dimension, a positive integer   [default: 2]    

`tau`   - Time Delay, a positive integer            [default: 1]    

`Bins`  - Histogram bin selection method for distance distribution,              an integer > 1 indicating the number of bins, or one of the              following strings {'sturges','sqrt','rice','doanes'}             [default: 'sturges'] 

`Logx`  - Logarithm base, a positive scalar         [default: 2]                 ** enter 0 for natural log**

`Norm`  - Normalisation of DistEn value:             [false]  no normalisation.             [true]   normalises w.r.t # of histogram bins [default] 

# See also `XSampEn`, `XApEn`, `XPermEn`, `XCondEn`, `DistEn`, `DistEn2D`, `XMSEn`

# References:

```
  [1] Yuanyuan Wang and Pengjian Shang,
      "Analysis of financial stock markets through the multiscale
      cross-distribution entropy based on the Tsallis entropy."
      Nonlinear Dynamics 
      94.2 (2018): 1361-1376.
```
