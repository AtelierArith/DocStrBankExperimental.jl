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

シンボリック回帰問題に対する可能な解の空間を探索するためにREINFORCEアルゴリズムを使用します。
