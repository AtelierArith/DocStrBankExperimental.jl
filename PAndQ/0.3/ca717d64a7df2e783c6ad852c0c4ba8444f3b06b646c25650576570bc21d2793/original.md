```
is_tautology(p)
```

Return a `Bool`ean indicating whether the given proposition is logically equivalent to a [`tautology`](@ref).

# Examples

```jldoctest
julia> is_tautology(⊤)
true

julia> @atomize is_tautology(p)
false

julia> @atomize is_tautology(¬(p ∧ ¬p))
true
```
