```
XCond, SEw, SEz = XCondEn(Sig1, Sig2)
```

Returns the corrected cross-conditional entropy estimates (`XCond`) and the corresponding Shannon entropies (m: SEw, m+1: SEz) for m = [1,2]  estimated for the data sequences contained in `Sig1` and `Sig2` using the default parameters:  embedding dimension = 2, time delay = 1, number of symbols = 6,  logarithm = natural ** Note: XCondEn is direction-dependent. Therefore, the order of the data sequences `Sig1` and `Sig2` matters. If `Sig1` is the sequence 'y', and `Sig2` is the second sequence 'u', the `XCond` is the amount of information carried by y(i) when the pattern u(i) is found.**

```
XCond, SEw, SEz = XCondEn(Sig1::Union{AbstractMatrix{T}, AbstractVector{T}} where T<:Real, Sig2::Union{AbstractVector{T} where T<:Real, Nothing} = nothing; m::Int=2, tau::Int=1, c::Int=6, Logx::Real=exp(1), Norm::Bool=false)
```

Returns the corrected cross-conditional entropy estimates (`XCond`) for the data sequences contained in `Sig1` and `Sig2` using the specified 'keyword' arguments:

# Arguments:

`m`     - Embedding Dimension, an integer > 1        [default: 2]  

`tau`   - Time Delay, a positive integer             [default: 1]  

`c`     - Number of symbols, an integer > 1          [default: 6]  

`Logx`  - Logarithm base, a positive scalar          [default: natural] 

`Norm`  - Normalisation of `XCond` values:              [false]  no normalisation                  [default]

```
        [true]   normalises w.r.t cross-Shannon entropy.
```

# See also `XFuzzEn`, `XSampEn`, `XApEn`, `XPermEn`, `CondEn`, `XMSEn`

# References:

```
[1] Alberto Porta, et al.,
    "Conditional entropy approach for the evaluation of the 
    coupling strength." 
    Biological cybernetics 
    81.2 (1999): 119-129.
```
