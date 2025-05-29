```
missingReferences(ffp::FilterFitPacket, elms::Vector{Element}, e0::Float64, ampl=1.0e-5)
```

`FilterFitPacket` から `FilteredReference` が欠落している ROI を含む `Vector{Tuple{Vector{CharXRay}, UnitRange{Int64}}}` を返します。
