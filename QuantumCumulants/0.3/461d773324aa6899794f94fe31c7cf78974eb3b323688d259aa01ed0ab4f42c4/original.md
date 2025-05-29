```
struct Spectrum
```

Type representing the spectrum, i.e. the Fourier transform of a [`CorrelationFunction`](@ref) in steady state.

To actually compute the spectrum at a frequency `ω`, construct the type on top of a correlation function and call it with `Spectrum(c)(ω,usteady,p0)`.
