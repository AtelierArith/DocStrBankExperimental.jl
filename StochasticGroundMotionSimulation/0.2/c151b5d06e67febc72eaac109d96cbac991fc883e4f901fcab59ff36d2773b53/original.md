```
fourier_source(f::T, m::S, src::SourceParameters) where {S<:Real,T<:Float64}
```

Source Fourier Amplitude Spectrum of displacement, without the constant term. This simply includes the seismic moment and the source spectral shape.

See also: [`fourier_source_shape`](@ref)
