```
check(a::Atom, i::AbstractVector)
```

Returns a truth value indicating whether or not that [`Atom`](@ref)  is contained in the passed vector.

# Examples

```julia-repl
julia> check(Atom(1), [1,2,4])
true

julia> check(Atom(5), [2,3,4])
false
```

See also [`Atom`](@ref).
