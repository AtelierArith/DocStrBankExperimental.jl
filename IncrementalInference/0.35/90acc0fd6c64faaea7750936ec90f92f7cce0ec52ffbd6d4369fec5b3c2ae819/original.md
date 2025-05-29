```julia
solveFactorParametric(
    dfg,
    fct,
    srcsym_vals,
    trgsym;
    solveKey,
    evaltmpkw...
)

```

Helper function to propagate a parametric estimate along a factor chain.   This function takes and returns variable values as coordinates.

Notes

  * Not used during MM-iSAM inference.
  * Expected uses are for user analysis of factors and estimates.
  * real-time dead reckoning chain prediction.
  * Parametric binary factor utility function, used by DRT

DevNotes

  * TODO ensure type stability, likely returning types `Any` at this time.
  * TODO MeanMaxPPE currently stored as coordinates, complicating fast calculation.

Related: [`getMeasurementParametric`](@ref), [`approxConvBelief`](@ref), [`MutablePose2Pose2Gaussian`](@ref)
