```julia
generateGraph_Helix2D!(; ...)
generateGraph_Helix2D!(
    numposes;
    posesperturn,
    graphinit,
    useMsgLikelihoods,
    solverParams,
    dfg,
    radius,
    spine_t,
    xr_t,
    yr_t,
    poseRegex,
    μ0,
    refKey,
    Qd,
    postpose_cb
)

```

Generalized canonical graph generator function for helix patterns.

Notes

  * assumes poses are labeled according to r"x\d+"
  * Gradient (i.e. angle) calculations are on the order of 1e-8.
  * Use callback `spine_t(t)::Complex` to modify how the helix pattern is moved in x, y along the progression of `t`,

      * See related wrapper functions for convenient generators of helix patterns in 2D,
      * Real valued `xr_t(t)` and `yr_t(t)` can be modified (and will override) complex valued `spine_t` instead.
  * use `postpose_cb = (fg_, lastestpose) -> ...` for additional user features after each new pose
  * can be used to grow a graph with repeated calls, but keyword parameters are assumed identical between calls.

See also: [`generateGraph_Helix2DSlew!`](@ref), [`generateGraph_Helix2DSpiral!`](@ref), [`generateGraph_Beehive!`](@ref)
