```
  Cond, SEw, SEz = CondEn(Sig)
```

Returns the corrected conditional entropy estimates (`Cond`) and the   corresponding Shannon entropies (m: `SEw`, m+1: `SEz`) for m = [1,2]    estimated from the data sequence (`Sig`) using the default  parameters:   embedding dimension = 2, time delay = 1, symbols = 6, logarithm = natural,   normalisation = false   *Note: CondEn(m=1) returns the Shannon entropy of `Sig`.*

```
  Cond, SEw, SEz = CondEn(Sig::AbstractArray{T,1} where T<:Real; m::Int=2, tau::Int=1, c::Int=6, Logx::Real=exp(1), Norm::Bool=false)
```

Returns the corrected conditional entropy estimates (`Cond`) from the data   sequence (`Sig`) using the specified 'keyword' arguments:

# Arguments:

`m`     - Embedding Dimension, an integer > 1  

`tau`   - Time Delay, a positive integer  

`c`     - # of symbols, an integer > 1  

`Logx`  - Logarithm base, a positive scalar  

`Norm`  - Normalisation of CondEn value:  

```
        [false]  no normalisation - default
        [true]   normalises w.r.t Shannon entropy of data sequence `Sig`
```

# See also `XCondEn`, `MSEn`, `PermEn`, `DistEn`, `XPermEn`

# References:

```
  [1] Alberto Porta, et al.,
      "Measuring regularity by means of a corrected conditional
      entropy in sympathetic outflow." 
      Biological cybernetics 
      78.1 (1998): 71-78.
```
