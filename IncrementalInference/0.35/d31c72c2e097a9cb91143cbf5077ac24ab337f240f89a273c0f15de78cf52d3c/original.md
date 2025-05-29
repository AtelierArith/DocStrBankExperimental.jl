```julia
setPPE!(variable)
setPPE!(variable, solveKey)
setPPE!(variable, solveKey, ppeType)
setPPE!(variable, solveKey, ppeType, newPPEVal)

```

Calculate new and then set PPE estimates for variable from some distributed factor graph.

DevNotes

  * TODO solve key might be needed if one only wants to update one
  * TODO consider a more fiting name.
  * guess it would make sense that :default=>variableNodeData, goes with :default=>MeanMaxPPE

Aliases

  * `setVariablePosteriorEstimates!`

DevNotes:

JT - TODO if subfg is in the cloud or from another fg it has to be updated it feels like a waste to update the whole variable for one field. currently i could find mergeUpdateVariableSolverData() might be handy to use a setter such as updatePointParametricEst(dfg, variable, solverkey) This might also not be the correct place, if it is uncomment: ``if (subfg <: InMemoryDFGTypes)   updateVariable!(subfg, var) end`

Related

[`calcPPE`](@ref), getVariablePPE, (updatePPE! ?)
