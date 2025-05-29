```
is_equisatisfiable(p, q)
```

Return a `Bool`ean indicating whether the predicate [`is_satisfiable`](@ref) is congruent for both propositions.

# Examples

```jldoctest
julia> is_equisatisfiable(⊤, ⊥)
false

julia> @atomize is_equisatisfiable(p, q)
true
```
