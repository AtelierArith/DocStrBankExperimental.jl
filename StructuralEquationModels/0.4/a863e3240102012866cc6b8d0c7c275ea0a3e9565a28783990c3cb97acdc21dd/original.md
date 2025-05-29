```
se_bootstrap(sem_fit::SemFit; n_boot = 3000, data = nothing, kwargs...)
```

Return boorstrap standard errors. Only works for single models.

# Arguments

  * `n_boot`: number of boostrap samples
  * `data`: data to sample from. Only needed if different than the data from `sem_fit`
  * `kwargs...`: passed down to `replace_observed`
