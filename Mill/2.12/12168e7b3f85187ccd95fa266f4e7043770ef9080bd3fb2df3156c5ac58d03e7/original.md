```
BagModel(im, a, bm=identity)
```

Construct a [`BagModel`](@ref) from the arguments. `im` should be [`AbstractMillModel`](@ref), `a` [`AbstractAggregation`](@ref) or [`BagCount`](@ref), and `bm` [`ArrayModel`](@ref).

It is also possible to pass any function as `im` instead of a model node. In that case, it is wrapped into an [`ArrayNode`](@ref).

# Examples

```jldoctest
julia> m = BagModel(ArrayModel(Dense(3, 2)), SegmentedMeanMax(2), Dense(4, 2))
BagModel ↦ [SegmentedMean(2); SegmentedMax(2)] ↦ Dense(4 => 2)  4 arrays, 14 params, 224 bytes
  ╰── ArrayModel(Dense(3 => 2))  2 arrays, 8 params, 120 bytes

julia> m = BagModel(Dense(4, 3), BagCount(SegmentedMean(3)))
BagModel ↦ BagCount(SegmentedMean(3)) ↦ identity  1 arrays, 3 params (all zero), 52 bytes
  ╰── ArrayModel(Dense(4 => 3))  2 arrays, 15 params, 148 bytes
```

See also: [`AbstractMillModel`](@ref), [`AbstractAggregation`](@ref), [`BagCount`](@ref),     [`AbstractBagNode`](@ref), [`BagNode`](@ref), [`WeightedBagNode`](@ref).
