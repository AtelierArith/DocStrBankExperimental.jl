ZygoteAdjoint <: AbstractAdjointSensitivityAlgorithm{nothing,true,nothing}

An implementation of discrete adjoint sensitivity analysis using the Zygote.jl source-to-source AD directly on the differential equation solver.

## Constructor

```julia
ZygoteAdjoint()
```

## SciMLProblem Support

Currently fails on almost every solver.
