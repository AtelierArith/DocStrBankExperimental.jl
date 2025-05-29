```
Window{S,T}
```

Data type for FBP apodizing windows, with given window `shape::S` and `cutoff::T`.

```jldoctest
julia> Window(Hamming(), 0.8)
Window{Hamming, Float64}(Hamming(), 0.8)
```
