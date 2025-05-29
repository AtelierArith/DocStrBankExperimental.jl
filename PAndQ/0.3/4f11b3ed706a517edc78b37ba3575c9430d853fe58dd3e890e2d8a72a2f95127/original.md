```
constants(f = 𝒾, xs)
```

Equivalent to `map(x -> @atomize $(f(x)), xs)`.

See also [`identical`](@ref).

# Examples

```jldoctest
julia> constants(1:2)
2-element Vector{PAndQ.Constant}:
 $(1)
 $(2)

julia> constants(string, 1:2)
2-element Vector{PAndQ.Constant}:
 $("1")
 $("2")
```
