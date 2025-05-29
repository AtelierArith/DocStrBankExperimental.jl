```
tseytin(p)
```

Apply the [Tseytin transformation](https://en.wikipedia.org/wiki/Tseytin_transformation) to the given proposition.

Using the [`normalize`](@ref) function to convert a proposition to conjunction normal form may result in an exponentially larger proposition, which can be intractable for sufficiently large propositions. The Tseytin transformation results in a linearly larger proposition that is in conjunction normal form and [`is_equisatisfiable`](@ref) to the original. However, it contains introduced variables and yields a subset of the [`solutions`](@ref) to the original proposition.

# Examples

```jldoctest
julia> is_equisatisfiable(⊤, tseytin(⊤))
true

julia> @atomize is_equisatisfiable(p, tseytin(p))
true

julia> is_equisatisfiable(⊥, tseytin(⊥))
true
```
