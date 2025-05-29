```
LazyRow(s::StructArray, i)
```

A lazy representation of `s[i]`. `LazyRow(s, i)` does not materialize the `i`th row but returns a lazy wrapper around it on which `getproperty` does the correct thing. This is useful when the row has many fields only some of which are necessary. It also allows changing columns in place.

See [`LazyRows`](@ref) to get an iterator of `LazyRow`s.

# Examples

```julia-repl
julia> t = StructArray((a = [1, 2], b = ["x", "y"]));

julia> LazyRow(t, 2).a
2

julia> LazyRow(t, 2).a = 123
123

julia> t
2-element StructArray(::Array{Int64,1}, ::Array{String,1}) with eltype NamedTuple{(:a, :b),Tuple{Int64,String}}:
 (a = 1, b = "x")
 (a = 123, b = "y")
```
