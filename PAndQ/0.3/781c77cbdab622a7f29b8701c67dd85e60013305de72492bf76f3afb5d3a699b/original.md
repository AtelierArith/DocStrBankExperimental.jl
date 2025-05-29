```
@variables(ps...)
```

Define variables and return a `Vector` containing them.

Examples

```jldoctest
julia> @variables p q
2-element Vector{PAndQ.Variable}:
 p
 q

julia> p
p

julia> q
q
```
