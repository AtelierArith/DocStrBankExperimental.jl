```
TransformQuery(name, query)
```

Simple transform query; references agents via underscores `_`.

See also [`@transform`](@ref).

# Examples

```julia
agent |> @transform(name=_.name)
agent |> @transform(name=_.name, _.age)
```
