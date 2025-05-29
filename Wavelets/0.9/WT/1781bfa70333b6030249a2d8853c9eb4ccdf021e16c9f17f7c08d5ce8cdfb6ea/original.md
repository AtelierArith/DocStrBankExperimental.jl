```
  (daughters, ω) = computeWavelets(n1::Integer, c::CFW{W}; T=Float64, J1::Int64=-1, dt::S=NaN, s0::V=NaN) where {S<:Real,
                                                               W<:WT.WaveletBoundary, V}
```

just precomputes the wavelets used by transform c::CFW{W}. For details, see cwt
