```
@insert assignment
```

Return a modified copy of deeply nested objects.

# Example

```jldoctest
julia> using Accessors

julia> t = (a=1, b=2);

julia> @insert t.c = 5
(a = 1, b = 2, c = 5)

julia> t
(a = 1, b = 2)
```

Supports the same syntax as [`@optic`](@ref). See also [`@set`](@ref).
