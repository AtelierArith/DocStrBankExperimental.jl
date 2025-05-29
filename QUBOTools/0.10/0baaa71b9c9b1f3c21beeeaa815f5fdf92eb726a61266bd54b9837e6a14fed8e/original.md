```
SampleSet{T,U}(
    data::Vector{Sample{T,U}},
    metadata::Union{Dict{String,Any},Nothing} = nothing;
    sense::Union{Sense,Symbol}   = :min,
    domain::Union{Domain,Symbol} = :bool,
) where {T,U}
```

Reference implementation of [`QUBOTools.AbstractSolution`](@ref).

It was inspired by D-Wave's SampleSet[^dwave], with a few tweaks. For example, samples are automatically sorted upon instantiation and repeated samples are merged by adding up their `reads` field. Also, the solution frame is stored, allowing for queries and [`cast`](@ref) operations.

[^dwave]: D-Wave Ocean SDK [{docs}](https://docs.ocean.dwavesys.com/en/stable/docs_dimod/reference/sampleset.html#id1)
