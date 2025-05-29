```
region(hss::HyperSpectrum{T, N}, ranges::AbstractRange...)::HyperSpectrum where {T<:Real,N}
```

Creates a view of a HyperSpectrum to represent the range of pixels within the `hss` HyperSpectrum.  Does not copy the data or properties so any modifications to the region are also made to `hss`.
