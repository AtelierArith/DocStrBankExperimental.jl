```
findsimilar(
    specs::AbstractArray{Spectrum{T}}; 
    atol = nothing, 
    rtol=1.5, 
    minspecs=3
)::Vector{Spectrum{T}}
findsimilar(
    specs::AbstractArray{Spectrum{T}},
    det::Detector,
    elm::Element; 
    atol = nothing, 
    rtol=1.5, 
    minspecs = 3
)::Vector{Spectrum{T}}
```

Filters a collection of spectra for the ones most similar to the average by removing the least similar spectrum sequentially until all the remaining spectra are either:

  * less than atol (if atol != nothing)
  * less than rtol * median(others) (if rtol != nothing)

when applying the 'similarity(...)` function to the spectrum and the sum of the other spectra.

This is useful for finding which of a set of replicate spectra are sufficiently similar  to each other.
