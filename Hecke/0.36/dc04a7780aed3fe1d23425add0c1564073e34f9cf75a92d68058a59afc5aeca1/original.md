```
torsion_free_rank(A::FinGenAbGroup) -> Int
```

Return the torsion free rank of $A$, that is, the dimension of the $\mathbf{Q}$-vectorspace $A \otimes_{\mathbf Z} \mathbf Q$.

See also [`rank`](@ref).

# Examples

```jldoctest
julia> G = abelian_group(5,0)
Z/5 x Z

julia> torsion_free_rank(G)
1

julia> rank(G)
2
```
