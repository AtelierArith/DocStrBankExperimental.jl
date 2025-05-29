```
@traitdef HasNonFrequencyDimension{D}
```

A trait indicating whether the data object has a non-frequency domain dimension.

# Example

```julia
@traitfn f(x::X) where {X; HasNonFrequencyDimension{X}} = "This spectrum has a non-frequency domain dimension!"
@traitfn f(x::X) where {X; Not{HasNonFrequencyDimension{X}}} = "This is a pure frequency-domain spectrum!"
```
