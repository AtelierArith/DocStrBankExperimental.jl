```
dosenormalize(spectrum::Spectrum{T}, dose=60.0)::Spectrum{T} where { T <: Real }
dosenormalize(spectrum::Spectrum{T}, dose=60.0)::Spectrum{Float64} where { T <: Integer }
```

Compute a spectrum which is `spectrum` rescaled to a live time times probe current equal to `dose`. Useful for setting spectra on an equivalent acquisition duration scale.
