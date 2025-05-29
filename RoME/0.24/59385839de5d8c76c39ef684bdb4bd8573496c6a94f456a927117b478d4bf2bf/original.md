```julia
mutable struct MutablePose2Pose2Gaussian <: DistributedFactorGraphs.AbstractManifoldMinimize
```

Specialized Pose2Pose2 factor type (Gaussian), which allows for rapid accumulation of odometry information as a branch on the factor graph.
