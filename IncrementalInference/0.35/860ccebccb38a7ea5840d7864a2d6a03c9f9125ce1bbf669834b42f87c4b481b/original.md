```julia
buildTreeFromOrdering!(
    dfg,
    elimOrder;
    drawbayesnet,
    solvable
)

```

Build Bayes/Junction/Elimination tree from a given variable ordering.

DevNotes

  * TODO use `solvable` filter during local graph copy step
  * TODO review `buildCliquePotentials` and rather incorporate into CSM, see #1083

Related

[`buildTreeReset!`](@ref)
