```
JointPrior{modelPriorType<:AbstractSimulatorPrior,likNames,likPriorTypes,axesType} <: AbstractSimulatorPrior
```

Represents the "joint" prior `p(θₘ,θₗ)` where `θ = [θₘ θₗ]` are the full set of parameters in the joint; distribution `p(x,θ)`. θₘ are the model (simulator) parameters and θₗ are the noise/error model parameters.
