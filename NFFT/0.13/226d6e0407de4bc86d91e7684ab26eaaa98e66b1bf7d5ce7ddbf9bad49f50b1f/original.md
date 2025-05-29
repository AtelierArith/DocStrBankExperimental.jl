```
    plan_nfft(k::Matrix{T}, N::NTuple{D,Int}, rest...;  kargs...)
```

compute a plan for the NFFT of a size-`N` array at the nodes contained in `k`.
