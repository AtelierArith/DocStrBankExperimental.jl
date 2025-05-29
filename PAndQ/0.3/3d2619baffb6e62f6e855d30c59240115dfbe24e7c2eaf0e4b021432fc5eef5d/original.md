```
is_falsifiable(p)
```

Return a `Bool`ean indicating whether `p` is [falsifiable](https://en.wikipedia.org/wiki/Falsifiability) (not logically equivalent to a [`tautology`](@ref)).

# Examples

```jldoctest
julia> is_falsifiable(⊥)
true

julia> @atomize is_falsifiable(p ∨ ¬p)
false

julia> @atomize is_falsifiable(p)
true

julia> @atomize is_falsifiable(p ∧ q)
true
```
