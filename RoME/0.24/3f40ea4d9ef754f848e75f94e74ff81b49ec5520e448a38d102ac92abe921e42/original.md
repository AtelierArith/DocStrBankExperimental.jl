```julia
generateGraph_ZeroPose(
;
    varType,
    graphinit,
    solverParams,
    dfg,
    doRef,
    useMsgLikelihoods,
    label,
    priorType,
    μ0,
    Σ0,
    priorArgs,
    solvable,
    variableTags,
    factorTags,
    postpose_cb
)

```

Generate a canonical factor graph with a Pose2 `:x0` and MvNormal with covariance `P0`.

Notes

  * Use e.g. `varType=Point2` to change from the default variable type `Pose2`.
  * Use `priorArgs::Tuple` to override the default input arguments to `priorType`.
  * Use callback `postpose_cb(g::AbstractDFG,lastpose::Symbol)` to call user operations after each pose step.
