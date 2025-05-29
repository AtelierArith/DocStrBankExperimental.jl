```
get_transformed_ensemble(sol::SimulatorInferenceSolution{<:EnsembleInferenceAlgorithm}, iter::Int=-1)
```

Fetches the transformed ensemble from the given solution object. For iterative algorithms, the optinal argument `iter` may be provided, which then retrieves the ensemble at the given iteration.
