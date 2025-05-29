```julia
stack_posterior_matrices(results)

```

Given a vector of `results`, each containing a property `posterior_matrix` (eg obtained from [`mcmc_with_warmup`](@ref) with the same sample length), return a lazy view as an array indexed by `[draw_index, chain_index, parameter_index]`.

This is useful as an input for eg `MCMCDiagnosticTools.ess_rhat`.

!!! note
    The ordering is not compatible with MCMCDiagnostictools version < 0.2.

