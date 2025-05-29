```julia
PerturbedAdditive(
    maximizer;
    ε,
    perturbation_dist,
    nb_samples,
    variance_reduction,
    seed,
    threaded,
    rng,
    dist_logdensity_grad
) -> Union{InferOpt.PerturbedOracle{InferOpt.AdditivePerturbation{Distributions.Normal{Float64}}, _A, _B, _C, Nothing, Random.TaskLocalRNG, Nothing} where {_A, _B, _C}, InferOpt.PerturbedOracle{InferOpt.AdditivePerturbation{Distributions.Normal{Float64}}, _A, _B, _C, InferOpt.NormalAdditiveGradLogdensity, Random.TaskLocalRNG, Nothing} where {_A, _B, _C}}

```

[`PerturbedOracle`](@ref) の加法的摂動のためのコンストラクタです。
