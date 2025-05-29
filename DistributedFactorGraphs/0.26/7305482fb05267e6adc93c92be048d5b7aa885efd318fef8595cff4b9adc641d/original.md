```julia
deepcopyGraph(, sourceDFG; ...)
deepcopyGraph(, sourceDFG, variableLabels; ...)
deepcopyGraph(
    ,
    sourceDFG,
    variableLabels,
    factorLabels;
    graphLabel,
    sessionId,
    kwargs...
)

```

Copy nodes from one graph into a new graph by making deepcopies. see [`copyGraph!`](@ref) for more detail. Related:

  * [`deepcopyGraph!`](@ref)
  * [`buildSubgraph`](@ref)
  * [`getNeighborhood`](@ref)
  * [`mergeGraph!`](@ref)
