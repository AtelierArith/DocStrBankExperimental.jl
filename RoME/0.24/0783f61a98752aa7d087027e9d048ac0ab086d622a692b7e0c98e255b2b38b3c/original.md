```julia
generateGraph_Boxes2D!(; ...)
generateGraph_Boxes2D!(
    numposes;
    graphinit,
    dfg,
    useMsgLikelihoods,
    length_x,
    length_y,
    slew_x,
    poseRegex,
    refKey,
    Qd,
    postpose_cb
)

```

Canonical graph generator for box shapes along x and y axes, with default behaviour slewing each new box along x-axes with 2/3 overlap on edges.

Notes

  * Function is still experimental
  * TODO currently `numposes` works in multiples of 4, for each corner of a new box – i.e. 8 –> 2 boxes.
  * Use `postpose_cb(fg, lastpose)` for additional behaviour after each pose variable has been added to the graph.

Related

[`generateGraph_ZeroPose`](@ref), [`generateGraph_Helix2DSlew!`](@ref), [`generateGraph_Hexagonal`](@ref)
