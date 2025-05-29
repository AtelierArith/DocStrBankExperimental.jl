```
EoE, AvEn, S2 = EnofEn(Sig)
```

Returns the entropy of entropy (`EoE`), the average Shannon entropy (`AvEn`), and the number of levels (`S2`) across all windows estimated from the data sequence (`Sig`) using the default parameters:  window length (samples) = 10, slices = 10, logarithm = natural,  heartbeat interval range (xmin, xmax) = (min(Sig), max(Sig))

```
EoE, AvEn, S2 = EnofEn(Sig::AbstractArray{T,1} where T<:Real; tau::Int=10, S::Int=10, Xrange::Tuple{Real,REal}, Logx::Real=exp(1))
```

Returns the entropy of entropy (`EoE`) estimated from the data sequence  (`Sig`)  using the specified 'keyword' arguments:

# Arguments:

`tau`    - Window length, an integer > 1 

`S`      - Number of slices (s1,s2), a two-element tuple of integers > 2 

`Xrange` - The min and max heartbeat interval, a two-element tuple where X[1] <= X[2]

`Logx`   - Logarithm base, a positive scalar  

# See also `SampEn`, `MSEn`, `ApEn`

# References:

```
[1] Chang Francis Hsu, et al.,
    "Entropy of entropy: Measurement of dynamical complexity for
    biological systems." 
    Entropy 
    19.10 (2017): 550.
```
