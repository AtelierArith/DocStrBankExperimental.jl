```julia
struct PriorIMUBias{T<:(IncrementalInference.SamplableBelief)} <: DistributedFactorGraphs.AbstractPrior
```

Introduce direct observations on all dimensions of a Pose2 variable:

## Example:

```julia
PriorIMUBias( MvNormal(zeros(6), Matrix(Diagonal(ones(6).^2))) )
```
