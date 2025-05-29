```
is_contingency(p)
```

Return a `Bool`ean indicating whether `p` is a [contingency](https://en.wikipedia.org/wiki/Contingency_(philosophy)) (not logically equivalent to a [truth value](@ref nullary_operators)).

# Examples

```jldoctest
julia> is_contingency(⊤)
false

julia> @atomize is_contingency(p ∧ ¬p)
false

julia> @atomize is_contingency(p)
true

julia> @atomize is_contingency(p ∧ q)
true
```
