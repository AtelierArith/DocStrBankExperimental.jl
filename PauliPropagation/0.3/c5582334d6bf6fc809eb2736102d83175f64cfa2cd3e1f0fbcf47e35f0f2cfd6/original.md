```
applymergetruncate!(gate, psum, aux_psum, thetas, param_idx; max_weight=Inf, min_abs_coeff=1e-10, max_freq=Inf, max_sins=Inf, customtruncfunc=nothing, kwargs...)
```

1st-level function below `propagate!` that applies one gate to all Pauli strings in `psum`, potentially using `aux_psum` in the process, and merges everything back into `psum`. Truncations are checked here after merging. This function can be overwritten for a custom gate if the lower-level functions `applytoall!`, `applyandadd!`, and `apply` are not sufficient.
