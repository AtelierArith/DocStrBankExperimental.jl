```
countEdges(F::T)::Vector{Int} where {T<:Flag}
```

Returns the Vector of numbers of set predicates in the Flag `F` for each `Predicate` type. For Graphs, this is the Vector with one element, the number of edges in the graph. Used when generating all Flags up to isomorphism of a given type to specify an upper bound on the number of set predicates.
