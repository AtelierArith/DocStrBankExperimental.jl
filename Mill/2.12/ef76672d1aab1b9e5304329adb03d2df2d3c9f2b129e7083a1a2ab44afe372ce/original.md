```
LazyModel([Name::Symbol], m::AbstractMillModel)
LazyModel{Name}(m::AbstractMillModel)
```

Construct a new [`LazyModel`](@ref) with name `Name`, and model `m`.

It is also possible to pass any function as `m` instead of a model node. In that case, it is wrapped into an [`ArrayNode`](@ref).

# Examples

```jldoctest
julia> LazyModel{:Sentence}(ArrayModel(Dense(2, 2)))
LazyModel{Sentence}
  ╰── ArrayModel(Dense(2 => 2))  2 arrays, 6 params, 112 bytes

julia> LazyModel(:Sentence, Dense(2, 2))
LazyModel{Sentence}
  ╰── ArrayModel(Dense(2 => 2))  2 arrays, 6 params, 112 bytes
```

See also: [`AbstractMillModel`](@ref), [`LazyNode`](@ref), [`Mill.unpack2mill`](@ref).
