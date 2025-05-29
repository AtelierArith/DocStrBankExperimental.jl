```julia
generateGraph_LineStep(
    lineLength;
    poseEvery,
    landmarkEvery,
    posePriorsAt,
    landmarkPriorsAt,
    sightDistance,
    vardims,
    noisy,
    graphinit,
    σ_pose_prior,
    σ_lm_prior,
    σ_pose_pose,
    σ_pose_lm,
    solverParams
)

```

連続的で線形のスカラーおよび多変量テストグラフ生成。ポーズIDが真の値と等しい線に従います。
