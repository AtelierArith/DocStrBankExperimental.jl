```julia
RandomSearch(
;
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
    alpha
)

```

Performs a random search over the space of possible solutions to the symbolic regression problem.
