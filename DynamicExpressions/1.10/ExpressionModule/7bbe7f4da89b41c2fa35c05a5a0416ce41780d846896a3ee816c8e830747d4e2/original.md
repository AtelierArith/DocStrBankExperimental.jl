```
get_metadata(ex::AbstractExpression)
```

Get the metadata of the expression, which might be a plain `NamedTuple`, or some combination of them, or other data. This should include everything other than that returned by [`get_contents`](@ref).
