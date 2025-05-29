```
LogDensityProblems.logdensity(
    inference_prob::SimulatorInferenceProblem;
    storage::SimulationData,
    kwargs...
)
```

Constructs an internal `LogDensityProblem` wrapper type that satisfies the `LogDensityProblems` interface.
