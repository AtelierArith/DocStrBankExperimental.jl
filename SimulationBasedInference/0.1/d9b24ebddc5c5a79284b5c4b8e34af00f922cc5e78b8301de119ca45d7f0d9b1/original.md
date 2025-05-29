```
SimulatorInferenceSolution{algType,probType,storageType}
```

Generic container for solutions to `SimulatorInferenceProblem`s. The type of `result` is method dependent and should generally correspond to the final state or product of the inference algorithm (e.g. posterior sampels). The field `output` should be an instance of `SimulationData`
