```
tophatfilter(
    charLabel::Union{CharXRayLabel,EscapeLabel, ReferenceLabel}
    filt::TopHatFilter{T},
    scale::T = one(T),
    tol::T = (T==Float32 ? 1.0f-5 : 1.0e-6)
)::FilteredReference
```

For filtering an ROI on a reference spectrum. Process a portion of a Spectrum with the specified filter.  Use a simple edge-based background model.

```
tophatfilter(
    labels::AbstractVector{ReferenceLabel},
    filt::TopHatFilter{T},
    scale::T = one(T),
    tol::T = (T==Float32 ? 1.0f-5 : 1.0e-6)
)::Vector{FilteredReference{T}}
```
