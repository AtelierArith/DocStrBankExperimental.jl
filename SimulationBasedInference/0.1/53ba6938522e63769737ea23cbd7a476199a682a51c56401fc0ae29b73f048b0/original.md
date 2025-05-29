```
SimulatorInferenceProblem{
    modelPriorType<:AbstractSimulatorPrior,
    uType,
    fwdProbType<:SimulatorForwardProblem,
    fwdSolverType,
    priorType<:JointPrior
} <: SciMLBase.AbstractSciMLProblem
```

Represents a generic simulation-based Bayesian inference problem for finding the posterior distribution over model parameters given some observed data.
