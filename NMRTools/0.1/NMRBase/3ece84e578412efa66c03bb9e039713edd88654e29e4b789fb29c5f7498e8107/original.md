```
coherenceorder(coherence)
```

Calculate the total coherence order.

# Examples

```jldoctest
julia> coherenceorder(SQ(H1))
1

julia> coherenceorder(MQ(((H1,1),(C13,1))))
2

julia> coherenceorder(MQ(((H1,1),(C13,-1))))
0

julia> coherenceorder(MQ(((H1,3),(C13,1))))
4

julia> coherenceorder(MQ(((H1,0),)))
0
```

See also [`Nucleus`](@ref), [`SQ`](@ref), [`MQ`](@ref).
