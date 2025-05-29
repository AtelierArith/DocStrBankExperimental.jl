```
FilterFitResult
```

Represents the result of fitting a FilteredUnknownW to a FilteredUnknown.

Struct elements

```
label::UnknownLabel  # Identifies the unknown
kratios::UncertainValues # Labeled with ReferenceLabel objects
roi::UnitRange{Int} # Range of channels fit
raw::Vector{T} # Raw spectrum data
residual::Deferred # Residual spectrum
peakback::Deferred # {Dict{ReferenceLabel,NTuple{3,Float64}}} with peak counts, background counts and counts/(nAs)
```

Use asa(DataFrame, ffr::FilterFitResult) to summarize in tabular form.
