```julia
PerturbedOracle(
    maximizer,
    dist_constructor;
    dist_logdensity_grad,
    nb_samples,
    variance_reduction,
    threaded,
    seed,
    rng,
    kwargs...
) -> InferOpt.PerturbedOracle{_A, _B, _C, _D, Nothing, Random.TaskLocalRNG, Nothing} where {_A, _B, _C, _D}

```

[`PerturbedOracle`](@ref) のコンストラクタ。
