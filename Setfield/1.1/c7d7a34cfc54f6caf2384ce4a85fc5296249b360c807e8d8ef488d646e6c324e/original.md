```
@set! assignment
```

Shortcut for `obj = @set obj...`.

# Example

```jldoctest
julia> using Setfield

julia> t = (a=1,)
(a = 1,)

julia> @set! t.a=2
(a = 2,)

julia> t
(a = 2,)
```
