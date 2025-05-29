```julia
struct PartialPriorYawPose2{T<:(IncrementalInference.SamplableBelief)} <: DistributedFactorGraphs.AbstractPrior
```

Constrain only the yaw angle of a Pose2, generally used for Gyrocompass, Magnetometer, Dual-GNSS heading type measurements, or any other similar construct.
