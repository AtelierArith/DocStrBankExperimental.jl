```
variationinfos(
    query::Union{SAM.Record,BAM.Record}, reference::NucleotideSeq
) -> Vector{VariationInfo}
variationinfos(
    query::Union{AbstractString,AbstractPath},
    reference::Union{AbstractString,AbstractPath}
) -> Vector{VariationInfo}
```

Calls `Variation`s based on the alignments in `query` against `reference`, and returns every variation call found within `query` as a `Vector{VariationInfo}`
