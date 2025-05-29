```
is_truth(p)
```

Return a `Bool`ean indicating whether given proposition is logically equivalent to a [truth value](@ref nullary_operators).

# Examples

```jldoctest
julia> is_truth(⊤)
true

julia> @atomize is_truth(p ∧ ¬p)
true

julia> @atomize is_truth(p)
false

julia> @atomize is_truth(p ∧ q)
false
```
