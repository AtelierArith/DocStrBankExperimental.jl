```julia
getTreeAllFrontalSyms(_, tree)

```

Return one symbol (a frontal variable) from each clique in the `::BayesTree`.

Notes

  * Frontal variables only occur once in a clique per tree, therefore is a unique identifier.

Related:

whichCliq, printCliqHistorySummary
