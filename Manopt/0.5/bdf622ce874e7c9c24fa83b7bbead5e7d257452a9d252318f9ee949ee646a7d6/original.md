```
StopWhenBestCostInGenerationConstant <: StoppingCriterion
```

Stop if the range of the best objective function values of the last `iteration_range` generations is zero. This corresponds to `EqualFUnValues` condition from [Hansen:2023](@cite).

See also `StopWhenPopulationCostConcentrated`.
