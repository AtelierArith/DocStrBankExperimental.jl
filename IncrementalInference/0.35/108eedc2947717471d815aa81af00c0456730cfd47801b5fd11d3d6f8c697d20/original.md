```julia
getClique(tree, cId)

```

Return the TreeClique node object that represents a clique in the Bayes (Junction) tree, as defined by one of the frontal variables `frt<:AbstractString`.

Notes

  * Frontal variables only occur once in a clique per tree, therefore is a unique identifier.

Related:

getCliq, getTreeAllFrontalSyms
