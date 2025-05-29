```julia
approxConvBelief(dfg, from, target; ...)
approxConvBelief(
    dfg,
    from,
    target,
    measurement;
    solveKey,
    N,
    tfg,
    setPPEmethod,
    setPPE,
    path,
    skipSolve,
    nullSurplus
)

```

Calculate the sequential series of convolutions in order as listed by `fctLabels`, and starting from the  value already contained in the first variable.  

Notes

  * `target` must be a variable.
  * The ultimate `target` variable must be given to allow path discovery through n-ary factors.
  * Fresh starting point will be used if first element in `fctLabels` is a unary `<:AbstractPrior`.
  * This function will not change any values in `dfg`, and might have slightly less speed performance to meet this requirement.
  * pass in `tfg` to get a recoverable result of all convolutions in the chain.
  * `setPPE` and `setPPEmethod` can be used to store PPE information in temporary `tfg`

DevNotes

  * TODO strong requirement that this function is super efficient on single factor/variable case!
  * FIXME must consolidate with `accumulateFactorMeans`
  * TODO `solveKey` not fully wired up everywhere yet

      * tfg gets all the solveKeys inside the source `dfg` variables
  * TODO add a approxConv on PPE option

      * Consolidate with [`accumulateFactorMeans`](@ref), `approxConvBinary`

Related

[`approxDeconv`](@ref), `findShortestPathDijkstra`
