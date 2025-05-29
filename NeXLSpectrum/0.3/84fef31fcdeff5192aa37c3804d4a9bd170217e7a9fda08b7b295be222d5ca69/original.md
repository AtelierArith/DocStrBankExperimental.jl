```
extents(cxrs::AbstractVector{<:SpectrumFeature},det::Detector,ampl::Float64)::Vector{UnitRange{Int}}
```

Determine the contiguous ranges of channels over which the specified collection of X-rays will be measured on the specified detector.  The ampl determines the extent of each peak.
