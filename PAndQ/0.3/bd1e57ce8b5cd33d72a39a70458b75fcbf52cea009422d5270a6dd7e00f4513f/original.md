```
is_contradiction(p)
```

Return a `Bool`ean indicating whether the given proposition is logically equivalent to a [`contradiction`](@ref).

# Examples

```jldoctest
julia> is_contradiction(⊥)
true

julia> @atomize is_contradiction(p)
false

julia> @atomize is_contradiction(p ∧ ¬p)
true
```
