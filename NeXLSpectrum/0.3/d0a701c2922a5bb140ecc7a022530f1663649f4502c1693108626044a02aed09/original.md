```
missingReferences(ffp::FilterFitPacket, elms::Vector{Element}, e0::Float64, ampl=1.0e-5)
```

Returns a `Vector{Tuple{Vector{CharXRay}, UnitRange{Int64}}}` containing the ROIs for which a  `FilteredReference` is missing from the `FilterFitPacket`.
