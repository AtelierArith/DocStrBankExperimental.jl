```
mutable struct PopDataInfo
    samples::Int64
    sampeinfo::DataFrame
    loci::Int64
    locusinfo::DataFrame
    populations::Int64
    ploidy::Union{Int8, Vector{Int8}}
    biallelic::Bool
end
```

The data struct used internally as `PopData.metadata` fields to store basic information about the `PopData` for easy access.
