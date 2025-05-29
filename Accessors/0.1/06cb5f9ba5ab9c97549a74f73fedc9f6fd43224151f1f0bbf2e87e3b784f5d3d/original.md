```
@reset assignment
```

Shortcut for `obj = @set obj...`.

# Example

```jldoctest
julia> using Accessors

julia> t = (a=1,)
(a = 1,)

julia> @reset t.a=2
(a = 2,)

julia> t
(a = 2,)
```

Supports the same syntax as [`@optic`](@ref). See also [`@set`](@ref).
