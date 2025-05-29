```julia
generateGraph_Beehive!(; ...)
generateGraph_Beehive!(
    poseCountTarget;
    graphinit,
    dfg,
    useMsgLikelihoods,
    solvable,
    refKey,
    addLandmarks,
    landmarkSolvable,
    poseRegex,
    pose0,
    yaw0,
    μ0,
    postpose_cb,
    locality,
    atol
)

```

Pretend a bee is walking in a hive where each step (pose) follows one edge of an imaginary honeycomb lattice,  and at after each step a new direction left or right is stochastically chosen and the process repeats.

Notes

  * The keyword `locality=1` is a positive `::Real` ∈ [0,∞) value, where higher numbers imply direction decisions are more sticky for multiple steps.
  * Use keyword callback function `postpose_cb = (fg, lastpose) -> ...` to hook in your own features right after each new pose step.

DevNotes

  * TODO rewrite as a recursive generator function instead.

See also: [`generateGraph_Honeycomb!`](@ref), [`generateGraph_Hexagonal`](@ref), [`generateGraph_ZeroPose`](@ref)
