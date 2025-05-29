```
wavelet(wave::ContWaveClass; Q=8, boundary::WaveletBoundary=DEFAULT_BOUNDARY,
averagingType::Average = Father(), averagingLength = 4,
frameBound=1, p=Inf, β=4, kwargs...)
```

A constructor for the `CWT` type, using keyword rather than positional options.
