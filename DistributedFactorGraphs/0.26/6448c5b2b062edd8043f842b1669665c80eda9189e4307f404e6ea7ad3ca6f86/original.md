```julia
buildSubgraph(, dfg, variableFactorLabels; ...)
buildSubgraph(
    ,
    dfg,
    variableFactorLabels,
    distance;
    solvable,
    graphLabel,
    sessionId,
    kwargs...
)

```

Build a deep subgraph copy from the DFG given a list of variables and factors and an optional distance. Note: Orphaned factors (where the subgraph does not contain all the related variables) are not returned. Related:

  * [`copyGraph!`](@ref)
  * [`getNeighborhood`](@ref)
  * [`deepcopyGraph`](@ref)
  * [`mergeGraph!`](@ref)

Dev Notes

  * Bulk vs node for node: a list of labels are compiled and the sugraph is copied in bulk.
