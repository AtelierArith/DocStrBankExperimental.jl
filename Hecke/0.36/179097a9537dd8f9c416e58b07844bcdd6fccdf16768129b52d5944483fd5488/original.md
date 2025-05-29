```
is_neat(U::FinGenAbGroup, G::FinGenAbGroup) -> Bool
```

A subgroup `U` of `G` is called neat if for all primes `p` an element in `U` that is in the image of the multiplication by `p` map of `G` is also a multiple of an element in `U`.

See also: [`is_pure`](@ref)

# EXAMPLES

```julia
julia> G = abelian_group([2, 8]);

julia> U, _ = sub(G, [G[1] + 2*G[2]]);

julia> is_neat(U, G)
true

julia> is_pure(U, G)
false
```
