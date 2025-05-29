```julia
generateGraph_TwoPoseOdo(
;
    solverParams,
    varType,
    solvable,
    doRef,
    postpose_cb,
    dfg,
    addlandmark,
    fg,
    graphinit
)

```

Build a basic factor graph in Pose2 with two `Pose2` and one landmark `Point2` variables, along with `PriorPose2` on `:x0` and `Pose2Pose2` to `:x1`.  Also a `Pose2Point2BearingRange` to landmark `:l1`.

DevNotes

  * TODO standardize to latest and greatest generator api pattern

See also: [`buildGraphChain!`](@ref)
