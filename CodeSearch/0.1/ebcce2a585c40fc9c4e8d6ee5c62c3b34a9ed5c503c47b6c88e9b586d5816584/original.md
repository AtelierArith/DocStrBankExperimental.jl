```
indices(m)
```

Return the indices into a source datastructure that a view is derived from.

# Examples

```jldoctest
julia> m = match(j"x/*", "4 + x/2")
CodeSearch.Match((call-i x / 2), captures=[2])

julia> indices(m)
4:7

julia> c = m[1]
line:col│ tree        │ file_name
   1:7  │2


julia> indices(c)
7:7
```
