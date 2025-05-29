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

シンボリック回帰問題に対する可能な解の空間をランダムに探索します。
