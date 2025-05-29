```
BagNode(d, b, m=nothing)
```

Construct a new [`BagNode`](@ref) with data `d`, bags `b`, and metadata `m`.

`d` is either an [`AbstractMillNode`](@ref) or `missing`. Any other type is wrapped in an [`ArrayNode`](@ref).

If `b` is an `AbstractVector`, [`Mill.bags`](@ref) is applied first.

# Examples

```jldoctest
julia> BagNode(ArrayNode(maybehotbatch([1, missing, 2], 1:2)), AlignedBags([1:1, 2:3]))
BagNode  2 obs
  ╰── ArrayNode(2×3 MaybeHotMatrix with Union{Missing, Bool} elements)  3 obs

julia> BagNode(randn(2, 5), [1, 2, 2, 1, 1])
BagNode  2 obs
  ╰── ArrayNode(2×5 Array with Float64 elements)  5 obs
```

See also: [`WeightedBagNode`](@ref), [`AbstractBagNode`](@ref),     [`AbstractMillNode`](@ref), [`BagModel`](@ref).
