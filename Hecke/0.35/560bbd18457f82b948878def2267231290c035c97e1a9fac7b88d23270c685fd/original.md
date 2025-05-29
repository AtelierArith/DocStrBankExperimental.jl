```
group_algebra(K::Ring, G::Group; cached::Bool = true) -> GroupAlgebra
```

Return the group algebra of the group $G$ over the ring $R$. Shorthand syntax for this construction is `R[G]`.

# Examples

```jldoctest
julia> QG = group_algebra(QQ, small_group(8, 5))
Group algebra
  of generic group of order 8 with multiplication table
  over rational field
```
