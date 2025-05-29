```
LazyRows(s::StructArray)
```

An iterator of [`LazyRow`](@ref)s of `s`.

# Examples

```julia-repl
julia> map(t -> t.b ^ t.a, LazyRows(t))
2-element Array{String,1}:
 "x"
 "yy"
```
