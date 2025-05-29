```julia
struct PriorPose2{T<:(IncrementalInference.SamplableBelief)} <: DistributedFactorGraphs.AbstractPrior
```

Introduce direct observations on all dimensions of a Pose2 variable:

## Example:

```julia
PriorPose2( MvNormal([10; 10; pi/6.0], Matrix(Diagonal([0.1;0.1;0.05].^2))) )
```
