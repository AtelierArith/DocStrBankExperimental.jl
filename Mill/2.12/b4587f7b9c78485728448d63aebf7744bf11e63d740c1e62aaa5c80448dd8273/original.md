```
Mill.unpack2mill(x::LazyNode)
```

Return a representation of [`LazyNode`](@ref) `x` using [`Mill.jl`](https://github.com/CTUAvastLab/Mill.jl) structures. Every custom [`LazyNode`](@ref) should have a special method as it is used in [`LazyModel`](@ref).

# Examples

```julia-repl
julia> function Mill.unpack2mill(ds::LazyNode{:Sentence})
    s = split.(ds.data, " ")
    x = NGramMatrix(reduce(vcat, s))
    BagNode(x, Mill.length2bags(length.(s)))
end;
```

```jldoctest
julia> LazyNode{:Sentence}(["foo bar", "baz"]) |> Mill.unpack2mill
BagNode  2 obs
  ╰── ArrayNode(2053×3 NGramMatrix with Int64 elements)  3 obs
```

See also: [`LazyNode`](@ref), [`LazyModel`](@ref).
