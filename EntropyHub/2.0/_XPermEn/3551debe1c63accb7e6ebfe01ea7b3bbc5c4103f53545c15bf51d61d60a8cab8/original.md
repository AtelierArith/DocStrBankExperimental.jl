```
 XPerm = XPermEn(Sig1, Sig2)
```

Returns the cross-permuation entropy estimates (`XPerm`) estimated betweeen  the data sequences contained in `Sig1` and `Sig2` using the default parameters:  embedding dimension = 3, time delay = 1, logarithm = base 2, 

```
 XPerm = XPermEn(Sig1::Union{AbstractMatrix{T}, AbstractVector{T}} where T<:Real, Sig2::Union{AbstractVector{T} where T<:Real, Nothing} = nothing; m::Int=3, tau::Int=1, Logx::Real=exp(1))
```

Returns the permutation entropy estimates (`XPerm`) estimated between the   data sequences contained in `Sig1` and `Sig2` using the specified 'keyword' arguments:

# Arguments:

`m`     - Embedding Dimension, an integer > 2   [default: 3]  

```
     **Note: XPerm is undefined for embedding dimensions < 3.**
```

`tau`   - Time Delay, a positive integer        [default: 1]    

`Logx`  - Logarithm base, a positive scalar     [default: 2]              ** enter 0 for natural log.**    

# See also `PermEn`, `XApEn`, `XSampEn`, `XFuzzEn`, `XMSEn`

# References:

```
 [1] Wenbin Shi, Pengjian Shang, and Aijing Lin,
     "The coupling analysis of stock market indices based on 
     cross-permutation entropy."
     Nonlinear Dynamics
     79.4 (2015): 2439-2447.
```
