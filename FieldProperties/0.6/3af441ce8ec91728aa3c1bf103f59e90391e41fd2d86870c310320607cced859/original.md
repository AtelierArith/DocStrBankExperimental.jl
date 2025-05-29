```
PropertyList{D}
```

Subtype of `AbstractPropertyList` that provides `getproperty` syntax for accessing the values of a dictionary.

## Examples

```jldoctest
julia> using FieldProperties

julia> m = PropertyList(; a = 1, b= 2)
PropertyList{Dict{Symbol,Any}} with 2 entries
    a: 1
    b: 2

julia> getindex(m, :a)
1

julia> get(m, :a, 3)
1

julia> get!(m, :a, 3)
1

julia> m.a
1

julia> m[:a] = 2
2

julia> m.a
2

julia> m.b
2

julia> m.b = 3
3

julia> m.b
3

julia> m.name = "ridiculously long name that we don't want to print everytime the other properties are printed.";


julia> m.suppress = (:name,)
(:name,)

julia> m
PropertyList{Dict{Symbol,Any}} with 4 entries
    a: 2
    b: 3
    name: <suppressed>
    suppress: (:name,)
```
