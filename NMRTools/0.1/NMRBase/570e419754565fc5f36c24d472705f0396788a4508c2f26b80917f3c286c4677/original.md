```
MQ(coherences, label=="")
```

Representation of a multiple-quantum coherence. Coherences are specified as a tuple of tuples, of the form `(nucleus, coherenceorder)`

# Examples

```jldoctest
julia> MQ(((H1,1), (C13,-1)), "ZQ")
MQ(((H1, 1), (C13, -1)), "ZQ")

julia> MQ(((H1,3), (C13,1)), "QQ")
MQ(((H1, 3), (C13, 1)), "QQ")
```

See also [`Nucleus`](@ref), [`SQ`](@ref).
