```
FrankenTuple{T<:Tuple, names, NT<:Tuple}
```

A `FrankenTuple` contains a `Tuple` of type `T` and a `NamedTuple` with names `names` and types `NT`. It acts like a cross between the two, like a partially-named tuple.

The named portion of a `FrankenTuple` can be accessed using `NamedTuple`, and the unnamed portion can be accessed with `Tuple`.

# Examples

```jldoctest
julia> ft = FrankenTuple((1, 2), (a=1, b=2))
FrankenTuple((1, 2), (a = 1, b = 2))

julia> Tuple(ft)
(1, 2)

julia> NamedTuple(ft)
(a = 1, b = 2)
```
