```
Bubb, H = BubbEn(Sig)
```

Returns the bubble entropy (`Bubb`) and the conditional Rényi entropy (`H`) estimates of dimension m = 2 from the data sequence (`Sig`) using  the default parameters:  embedding dimension = 2, time delay = 1, logarithm = natural 

```
Bubb, H = BubbEn(Sig::AbstractArray{T,1} where T<:Real; m::Int=2, tau::Int=1, Logx::Real=exp(1))
```

Returns the bubble entropy (`Bubb`) estimate of the data sequence (`Sig`)   using the specified 'keyword' arguments:

# Arguments:

`m`     - Embedding Dimension, an integer > 1   

```
      BubbEn returns estimates for each dimension [2,...,m]
```

`tau`   - Time Delay, a positive integer    

`Logx`  - Logarithm base, a positive scalar 

# See also `PhasEn`, `MSEn`

# References:

```
[1] George Manis, M.D. Aktaruzzaman and Roberto Sassi,
    "Bubble entropy: An entropy almost free of parameters."
    IEEE Transactions on Biomedical Engineering
    64.11 (2017): 2711-2718.
```
