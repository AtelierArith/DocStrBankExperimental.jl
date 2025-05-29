```
gyromagneticratio(n::Nucleus)
gyromagneticratio(c::Coherence)
```

Return the gyromagnetic ratio in Hz/T of a nucleus, or calculate the effective gyromagnetic ratio of a coherence. This is equal to the product of the individual gyromagnetic ratios with their coherence orders.

Returns `nothing` if not defined.

# Examples

```jldoctest
julia> gyromagneticratio(H1)
2.6752218744e8

julia> gyromagneticratio(SQ(H1))
2.6752218744e8

julia> gyromagneticratio(MQ(((H1,1),(C13,1))))
3.3480498744e8

julia> gyromagneticratio(MQ(((H1,0),)))
0.0
```

See also [`Nucleus`](@ref), [`Coherence`](@ref).
