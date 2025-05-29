```
AliasTable{T<:Unsigned=UInt64, I<:Integer=Int}(weights::AbstractVector{<:Real})
```

An efficient data structure for sampling from a discrete distribution.

Maps every value representable by `T` to a value of type `I` in `eachindex(wights)` such that the number of values maped to a given index of `weights` is proportional to the value at that index.

The mapping can be accessed directly via [`AliasTables.sample(x::T, at::AliasTable{T, I})`](@ref AliasTables.sample) or indirectly via the `Random` API: `rand(at)`, `rand(rng, at)`, `rand(at, dims...)`, etc.

See also [`AliasTables.set_weights!`](@ref)

# Example

```jldoctest; filter=[r" [1-3]"]
julia> at = AliasTable([1, 3, 1])
AliasTable([0x3333333333333334, 0x9999999999999999, 0x3333333333333333])

julia> rand(at, 5)
5-element Vector{Int64}:
 2
 3
 2
 2
 3
```
