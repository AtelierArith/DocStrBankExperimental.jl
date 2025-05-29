```
get_active_stopping_criteria(c)
```

returns all active stopping criteria, if any, that are within a [`StoppingCriterion`](@ref) `c`, and indicated a stop, that is their reason is nonempty. To be precise for a simple stopping criterion, this returns either an empty array if no stop is indicated or the stopping criterion as the only element of an array. For a [`StoppingCriterionSet`](@ref) all internal (even nested) criteria that indicate to stop are returned.
