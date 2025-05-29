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

Continuous, linear scalar and multivariate test graph generation. Follows a line with the pose id equal to the ground truth.
