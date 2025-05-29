```
fourier_source_shape(f::T, m::S, src::SourceParameters) where {S<:Real,T<:Float64}
```

Source shape of the Fourier Amplitude Spectrum of *displacement*, without the constant term or seismic moment. This simply includes the source spectral shape.

The nature of the source spectral shape depends upon `src.model`:

  * `:Brune` gives the single corner omega-squared spectrum (this is the default)
  * `:Atkinson_Silva_2000` gives the double corner spectrum of Atkinson & Silva (2000)
  * `:Beresnev_2019` gives a single-corner spectrum with arbitrary fall off rate related to `src.n` from Beresnev (2019)
