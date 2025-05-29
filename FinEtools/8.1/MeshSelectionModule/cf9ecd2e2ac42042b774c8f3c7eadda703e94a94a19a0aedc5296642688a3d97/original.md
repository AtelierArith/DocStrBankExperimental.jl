```
connectedelems(
    fes::AbstractFESet,
    node_list::Vector{IT},
    nmax::IT,
) where {IT<:Integer}
```

Extract the list of serial numbers of the fes connected to given nodes.
