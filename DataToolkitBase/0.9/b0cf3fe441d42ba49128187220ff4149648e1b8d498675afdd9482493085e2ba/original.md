```
resolve(identstr::AbstractString, parameters::Union{SmallDict{String, Any}, Nothing}=nothing;
        resolvetype::Bool=true, stack::Vector{DataCollection}=STACK)
```

Attempt to resolve the identifier given by `identstr` and `parameters` against each layer of the data `stack` in turn.
