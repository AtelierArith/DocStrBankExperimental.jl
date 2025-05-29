```
block(hss::HyperSpectrum{T,N,NP}, steps::NTuple{N, Int})::HyperSpectrum{T,N,NP} where {T<:Real, N, NP}
block(hss::HyperSpectrum{T,N,NP}, step::Int) where {T<:Real, N, NP}
```

Reduce the size of a HyperSpectrum by summing together blocks of adjacent pixels.  For example, `steps=(4,4)` would sum together blocks of 16 spectra in `hss` to form a single pixel in the resulting `Hyperspectrum`.
