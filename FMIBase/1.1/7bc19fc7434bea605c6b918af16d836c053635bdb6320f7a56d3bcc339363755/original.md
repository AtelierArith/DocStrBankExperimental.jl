```
stringToIntervalQualifier(::FMI3Struct, s::AbstractString)
```

Convert `s` ("intervalNotYetKnown", "intervalUnchanged", "intervalChanged") to the corresponding [`fmi3IntervalQualifier`](@ref).
