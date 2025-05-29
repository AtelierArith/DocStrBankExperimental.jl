```julia
GetRef(

) -> NamedTuple{(:id, :path), <:Tuple{UInt32, Union{Nothing, String}}}
GetRef(
    ctx
) -> NamedTuple{(:id, :path), <:Tuple{UInt32, Union{Nothing, String}}}

```

Get the current reference, with `id` and `path` properties.

# Examples

```julia
@register_test(engine, "foo", "bar") do ctx
    x = GetRef()
    @show x.id x.path
end
```
