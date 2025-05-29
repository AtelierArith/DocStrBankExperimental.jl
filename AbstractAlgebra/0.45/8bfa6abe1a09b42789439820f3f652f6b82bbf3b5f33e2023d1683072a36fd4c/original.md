```
pluralize(noun::String)
```

Return the plural form of a given english noun in singular.

This function employs certain heuristics and thus may not always obtain the correct pluralization. But it works well enough in the vast majority of cases.

# Examples

```jldoctest
julia> pluralize("generator")
"generators"

julia> pluralize("variety")
"varieties"
```
