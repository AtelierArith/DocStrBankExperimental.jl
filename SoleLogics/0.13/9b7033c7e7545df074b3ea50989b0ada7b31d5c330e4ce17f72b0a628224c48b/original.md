```
check(a::Atom, i::AbstractDict)
```

Returns the Boolean value corresponding to the atom passed as parameter.

# Examples

```julia-repl
julia> check(Atom(1), Dict([1 => ⊤, 2 => ⊥]))
true

julia> check(Atom(3), Dict([1 => ⊤, 2 => ⊥]))
false
```

See also [`Atom`](@ref).
