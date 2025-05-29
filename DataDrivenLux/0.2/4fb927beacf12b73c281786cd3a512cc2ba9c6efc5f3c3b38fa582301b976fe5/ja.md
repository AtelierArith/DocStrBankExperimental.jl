```julia
CrossEntropy(
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

離散最適化のためのクロスエントロピー法を使用して、可能な解の空間を探索します。
