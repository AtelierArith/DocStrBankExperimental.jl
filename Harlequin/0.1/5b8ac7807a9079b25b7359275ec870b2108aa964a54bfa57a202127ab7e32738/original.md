```
compute_residuals!(residuals, baseline_lengths, destriping_data, obs_list; comm=nothing, unseen=missing)
```

This function is used to compute the value of $A x - b$ at the beginning of the Conjugated-Gradient algorithm implemented in [`destripe!`](@ref).
