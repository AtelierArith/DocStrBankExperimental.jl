```
SimulatorInferenceProblem(
    prob::SimulatorForwardProblem,
    forward_solver,
    prior::AbstractSimulatorPrior,
    likelihoods::AbstractLikelihood...;
    metadata::Dict=Dict(),
)
```

Constructs a `SimulatorInferenceProblem` from the given forward problem, prior, and likelihoods. Additional user-specified metadata may be included in the `metadata` dictionary.
