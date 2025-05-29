```julia
Reinforce(
;
    reward,
    populationsize,
    functions,
    arities,
    n_layers,
    skip,
    loss,
    keep,
    use_protected,
    distributed,
    threaded,
    rng,
    optimizer,
    optim_options,
    observed,
    alpha,
    optimiser,
    ad_backend
)

```

Uses the REINFORCE algorithm to search over the space of possible solutions to the symbolic regression problem.
