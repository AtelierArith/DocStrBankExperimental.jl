```
LazyNode([Name::Symbol], d, m=nothing)
LazyNode{Name}(d, m=nothing)
```

Construct a new [`LazyNode`](@ref) with name `Name`, data `d`, and metadata `m`.

# Examples

```jldoctest
julia> LazyNode(:Codons, ["GGGCGGCGA", "CCTCGCGGG"])
LazyNode{:Codons, Vector{String}, Nothing}:
 "GGGCGGCGA"
 "CCTCGCGGG"
```

See also: [`AbstractMillNode`](@ref), [`LazyModel`](@ref), [`Mill.unpack2mill`](@ref).
