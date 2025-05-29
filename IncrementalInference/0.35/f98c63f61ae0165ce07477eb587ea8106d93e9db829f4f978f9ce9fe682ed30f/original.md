```julia
buildCliqSubgraph!(
    cliqSubFg,
    dfg,
    frontals,
    separators;
    solvable,
    verbose,
    solveKey
)

```

Specialized subgraph function for cliques to build a deep subgraph copy from the DFG given a list of frontals and separators. Dev notes:

  * TODO Since a clique should already have a list of frontals, seperators, and potentials (factors), this function should just be a light wrapper around copyGraph or buildSubgraph
  * TODO Send in clique and then extract frontals, separators and factors
  * TODO ability to limit which solveKeys to copy.
