```julia
struct PriorVelPos3{T<:(IncrementalInference.SamplableBelief)} <: DistributedFactorGraphs.AbstractPrior
```

Introduce direct observations on all dimensions of a Pose2 variable:

## Example:

```julia
PriorVelPos3( MvNormal(zeros(6), Matrix(Diagonal(ones(6).^2))) )
```
