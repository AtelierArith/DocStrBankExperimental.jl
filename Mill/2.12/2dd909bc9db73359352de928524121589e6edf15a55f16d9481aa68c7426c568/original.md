```
BagModel{T <: AbstractMillModel, A <: Union{AbstractAggregation, BagCount}, U}
    <: AbstractMillModel
```

A model node for processing [`AbstractBagNode`](@ref)s. It first applies its "instance (sub)model" `im` on every instance, then performs elementwise segmented aggregation `a` and finally applies the final model `bm` on the aggregated representation of every bag in the data node.

# Examples

```jldoctest; filter=r"\s*-?[0-9]+\.[0-9]+[\.]*\s*"
julia> Random.seed!(0);

julia> n = BagNode(ArrayNode(randn(Float32, 3, 2)), bags([0:-1, 1:2]))
BagNode  2 obs
  ╰── ArrayNode(3×2 Array with Float32 elements)  2 obs

julia> m = BagModel(ArrayModel(Dense(3, 2)), SegmentedMeanMax(2), Dense(4, 2))
BagModel ↦ [SegmentedMean(2); SegmentedMax(2)] ↦ Dense(4 => 2)  4 arrays, 14 params, 224 bytes
  ╰── ArrayModel(Dense(3 => 2))  2 arrays, 8 params, 120 bytes

julia> m(n)
2×2 Matrix{Float32}:
 0.0  1.05...
 0.0  0.49...

julia> m(n) == m.bm(m.a(m.im(n.data), n.bags))
true
```

See also: [`AbstractMillModel`](@ref), [`AbstractAggregation`](@ref), [`AbstractBagNode`](@ref),     [`BagNode`](@ref), [`WeightedBagNode`](@ref).
