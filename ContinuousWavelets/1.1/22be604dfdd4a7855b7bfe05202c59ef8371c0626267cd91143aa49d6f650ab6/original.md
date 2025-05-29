```
computeWavelets(n1::Integer, c::CWT{B,CT,W}; T = Float64, space = false) where {B<:WaveletBoundary,W,CT} -> daughters, ω
```

Precomputes the wavelets used by transform. For details, see cwt.
