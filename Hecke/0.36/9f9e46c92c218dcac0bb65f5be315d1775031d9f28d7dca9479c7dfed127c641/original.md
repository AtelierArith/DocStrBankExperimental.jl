```
psubgroups(g::FinGenAbGroup, p::Integer;
           subtype = :all,
           quotype = :all,
           index = -1,
           order = -1)
```

Return an iterator for the subgroups of $G$ of the specific form. Note that `subtype` (and `quotype`) is the type of the subgroup as an abelian $p$-group.
