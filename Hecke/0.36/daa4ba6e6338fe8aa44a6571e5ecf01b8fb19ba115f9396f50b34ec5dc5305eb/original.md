```
abelian_group(::Type{T} = FinGenAbGroup, M::ZZMatrix) -> FinGenAbGroup
```

Creates the abelian group with relation matrix `M`. That is, the group will have `ncols(M)` generators and each row of `M` describes one relation.
