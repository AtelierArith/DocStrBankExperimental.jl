```julia
struct PartitionSpace{T<:Integer, P<:EqualitySampler.AbstractPartitionSpace}
```

```julia
# constructor
PartitionSpace(k::T, ::Type{U} = EqualitySampler.DistinctPartitionSpace)
```

A type to represent the space of partitions. `EqualitySampler.AbstractPartitionSpace` indicates whether partitions should contains duplicates or be distinct. For example, the distinct iterator will return `[1, 1, 2]` but not `[2, 2, 1]` and `[1, 1, 3]`, which are returned when `P = EqualitySampler.DuplicatedPartitionSpace`.
