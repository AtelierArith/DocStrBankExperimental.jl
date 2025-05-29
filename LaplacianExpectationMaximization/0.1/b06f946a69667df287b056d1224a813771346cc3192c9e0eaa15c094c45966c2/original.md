```julia
simulate(
    model,
    parameters;
    n_steps,
    stop,
    init,
    tracked,
    rng,
    kw...
)

```

Returns a named tuple `(; data, logp)`. `stop(data, i)` is a boolean function that depends on the sequence of simulated `data` and the iteration counter `i`. If `tracked = true` the state of the model is saved for every step in the simulation. Additional keyword arguments `kw` are passed to the `sample` function.
