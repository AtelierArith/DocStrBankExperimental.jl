```
aref(v::AbstractArray)
```

Wraps an array, allowing mutating immutable plain data fields using the following syntax:

```julia
    aref(v)[i].a.b._i._j[] = val
```

The nested fields can be accessed using either the field name, or the field index prefixed with `_`. Except for the wrapped vector, every field in the chain must be immutable. The final type to be mutated must be bits type.

Examples:

```julia-repl
julia> a = [1, 2, 3];

julia> aref(a)[1][] = 4
4

julia> a
3-element Vector{Int64}:
 4
 2
 3

julia> b = [(tup=(1, 2.5), s="a"), (tup=(2, 4.5), s="b")];
 
julia> aref(b)[1].tup._2[] = Inf
Inf

julia> b
2-element Vector{NamedTuple{(:tup, :s), Tuple{Tuple{Int64, Float64}, String}}}:
 (tup = (1, Inf), s = "a")
 (tup = (2, 4.5), s = "b")

julia> aref(b)[2]._1._1[] *= 100
200

julia> b
2-element Vector{NamedTuple{(:tup, :s), Tuple{Tuple{Int64, Float64}, String}}}:
 (tup = (1, Inf), s = "a")
 (tup = (200, 4.5), s = "b")

julia> aref(b)[1].s[] = "invalid"
ERROR: The field type String (field s in NamedTuple{(:tup, :s), Tuple{Tuple{Int64, Float64}, String}}) is not immutable.
Stacktrace:
 ...
```
