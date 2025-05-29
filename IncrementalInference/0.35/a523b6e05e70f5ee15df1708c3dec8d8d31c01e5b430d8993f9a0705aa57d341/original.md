```julia
accumulateFactorMeans(dfg, fctsyms; solveKey)

```

Accumulate chains of binary factors–-potentially starting from a prior–-as a parameteric mean value only.

Notes

  * Not used during tree inference.
  * Expected uses are for user analysis of factors and estimates.
  * real-time dead reckoning chain prediction.
  * Returns mean value as coordinates

DevNotes

  * TODO consolidate with similar [`approxConvBelief`](@ref)
  * TODO compare consolidate with [`solveParametricConditionals`](@ref)
  * TODO compare consolidate with [`solveFactorParametric`](@ref)

Related:

[`approxConvBelief`](@ref), [`solveFactorParametric`](@ref), `RoME.MutablePose2Pose2Gaussian`
