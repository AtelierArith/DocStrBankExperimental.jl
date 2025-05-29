```
epgDephasing(F::Vector{T}, n=1) where T = circshift(F[:],n)
```

shifts the transverse dephasing states `F` corresponding to n dephasing-cycles.
