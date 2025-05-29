The abstract base type for asynchronous evaluators.

Asynchronous evaluator allows submitting fitness calculation requests via [`async_update_fitness!`](@ref) method that returns [`AbstractFitnessEvaluationJob`](@ref) object without waiting for the calculation completion. Job object could then be passed to [`sync_update_fitness`](@ref) that waits until fitnesses for all specified jobs is calculated.
