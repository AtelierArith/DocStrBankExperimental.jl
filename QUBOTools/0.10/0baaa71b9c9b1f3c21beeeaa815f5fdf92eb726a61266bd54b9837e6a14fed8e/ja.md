```
SampleSet{T,U}(
    data::Vector{Sample{T,U}},
    metadata::Union{Dict{String,Any},Nothing} = nothing;
    sense::Union{Sense,Symbol}   = :min,
    domain::Union{Domain,Symbol} = :bool,
) where {T,U}
```

[`QUBOTools.AbstractSolution`](@ref)の参照実装です。

これはD-WaveのSampleSet[^dwave]に触発されており、いくつかの調整が加えられています。たとえば、サンプルはインスタンス化時に自動的にソートされ、繰り返しのサンプルは`reads`フィールドを加算することでマージされます。また、ソリューションフレームが保存され、クエリや[`cast`](@ref)操作が可能です。

[^dwave]: D-Wave Ocean SDK [{docs}](https://docs.ocean.dwavesys.com/en/stable/docs_dimod/reference/sampleset.html#id1)
