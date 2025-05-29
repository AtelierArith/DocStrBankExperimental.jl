```
WeightedBagNode(d, b, w::Vector, m=nothing)
```

Construct a new [`WeightedBagNode`](@ref) with data `d`, bags `b`, vector of weights `w` and metadata `m`.

`d` is either an [`AbstractMillNode`](@ref) or `missing`. Any other type is wrapped in an [`ArrayNode`](@ref).

If `b` is an `AbstractVector`, [`Mill.bags`](@ref) is applied first.

# Examples

```jldoctest
julia> WeightedBagNode(ArrayNode(NGramMatrix(["s1", "s2"])), bags([1:2, 0:-1]), [0.2, 0.8])
WeightedBagNode  2 obs
  ╰── ArrayNode(2053×2 NGramMatrix with Int64 elements)  2 obs

julia> WeightedBagNode(zeros(2, 2), [1, 2], [1, 2])
WeightedBagNode  2 obs
  ╰── ArrayNode(2×2 Array with Float64 elements)  2 obs
```

See also: [`BagNode`](@ref), [`AbstractBagNode`](@ref), [`AbstractMillNode`](@ref), [`BagModel`](@ref).
