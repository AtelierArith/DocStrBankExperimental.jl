```
is_pure(U::FinGenAbGroup, G::FinGenAbGroup) -> Bool
```

A subgroup `U` of `G` is called pure if for all `n` an element in `U` that is in the image of the multiplication by `n` map of `G` is also a multiple of an element in `U`.

For finite abelian groups this is equivalent to `U` having a complement in `G`. They are also know as *isolated subgroups* and *serving subgroups*.

See also: [`is_neat`](@ref), [`has_complement`](@ref)

# EXAMPLES

```julia
julia> G = abelian_group([2, 8]);

julia> U, _ = sub(G, [G[1]+2*G[2]]);

julia> is_pure(U, G)
false

julia> U, _ = sub(G, [G[1]+4*G[2]]);

julia> is_pure(U)
true

julia> has_complement(U, G)[1]
true
```
