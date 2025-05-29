```
has_complement(f::FinGenAbGroupHom) -> Bool, FinGenAbGroupHom
has_complement(U::FinGenAbGroup, G::FinGenAbGroup) -> Bool, FinGenAbGroupHom
```

Given a map representing a subgroup of a group $G$, or a subgroup `U` of a group `G`, return either true and an injection of a complement in $G$, or false.

See also: [`is_pure`](@ref)
