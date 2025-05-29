```
is_satisfiable(p)
```

Return a `Bool`ean indicating whether `p` is [satisfiable](https://en.wikipedia.org/wiki/Satisfiability) (not logically equivalent to a [`contradiction`](@ref)).

# Examples

```jldoctest
julia> is_satisfiable(⊤)
true

julia> @atomize is_satisfiable(p ∧ ¬p)
false

julia> @atomize is_satisfiable(p)
true

julia> @atomize is_satisfiable(p ∧ q)
true
```
