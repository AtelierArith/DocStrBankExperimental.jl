```
async_update_fitness!(eval::AbstractAsyncEvaluator, candidates::Any;
                      force::Bool=false) ->
                      Union{AbstractFitnessEvaluationJob, Nothing}
```

Asynchronously calculate the fitnesses. *candidates* should support the `iterate()` interface and return [`Candidate`](@ref) elements.

Returns [`AbstractFitnessEvaluationJob`](@ref) or `nothing` if *candidates* does not contain any candidates.

# Arguments

  * `force::Bool`: force fitness calculation even if the candidate already has non-NA fitness

See also: [`sync_update_fitness`](@ref)
