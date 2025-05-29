```
probabilities(at::AliasTable{T}) -> Vector{T}
```

Recover the exact sampling weights from a given `AliasTable`. The returned values will sum to one more than `typemax(T)`, unless `at` is a constant distribution (e.g. `AliasTable([0,1,0])`), in which case the weights will sum to `typemax(T)`.

See also [`AliasTable`](@ref), [`AliasTables.sample`](@ref)

# Examples

```jldoctest
julia> at = AliasTable([1, 3, 1])
AliasTable([0x3333333333333334, 0x9999999999999999, 0x3333333333333333])

julia> AliasTables.probabilities(at)
3-element Vector{UInt64}:
 0x3333333333333334
 0x9999999999999999
 0x3333333333333333

julia> AliasTables.probabilities(AliasTable([0, 1, 0]))
3-element Vector{UInt64}:
 0x0000000000000000
 0xffffffffffffffff
 0x0000000000000000
```
