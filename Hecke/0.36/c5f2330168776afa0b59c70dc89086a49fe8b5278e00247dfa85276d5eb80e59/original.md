```
rank(A::FinGenAbGroup) -> Int
```

Return the rank of $A$, that is, the size of a minimal generating set for $A$.

See also [`torsion_free_rank`](@ref).

# Examples

```jldoctest
julia> G = abelian_group(5,0)
Z/5 x Z

julia> torsion_free_rank(G)
1

julia> rank(G)
2
```
