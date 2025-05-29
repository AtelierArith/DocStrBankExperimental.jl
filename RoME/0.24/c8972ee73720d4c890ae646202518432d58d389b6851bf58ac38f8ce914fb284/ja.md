```julia
generateGraph_Honeycomb!(; ...)
generateGraph_Honeycomb!(
    poseCountTarget;
    graphinit,
    dfg,
    useMsgLikelihoods,
    direction,
    solvable,
    refKey,
    addLandmarks,
    landmarkSolvable,
    atol,
    postpose_cb
)

```

予め決められたハニカム構造のグラフを生成します。

参照: [`generateGraph_Beehive!`](@ref), [`generateGraph_Hexagonal`](@ref)
