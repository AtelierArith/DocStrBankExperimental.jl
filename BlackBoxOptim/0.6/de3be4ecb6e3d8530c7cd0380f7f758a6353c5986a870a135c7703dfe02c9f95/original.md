```
sync_fitness_update([f], job::AbstractFitnessEvaluationJob,
                    eval::AbstractAsyncEvaluator)
```

Waits until fitnesses for `job` are calculated and optionally applies `f` function to each processed candidate.

See also: [`async_update_fitness!`](@ref), [`update_fitness!`](@ref).
