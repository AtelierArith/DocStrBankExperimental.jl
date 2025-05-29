```
rstar(
    rng::Random.AbstractRNG=Random.default_rng(),
    classifier,
    samples::AbstractArray{<:Real};
    subset::Real=0.7,
    split_chains::Int=2,
    verbosity::Int=0,
)
```

Compute the $R^*$ convergence statistic of the `samples` with the `classifier`.

`samples` is an array of draws with the shape `(draws, [chains[, parameters...]])`.`

This implementation is an adaption of algorithms 1 and 2 described by Lambert and Vehtari.

The `classifier` has to be a supervised classifier of the MLJ framework (see the [MLJ documentation](@extref MLJ list_of_supported_models) for a list of supported models). It is trained with a `subset` of the samples from each chain. Each chain is split into `split_chains` separate chains to additionally check for within-chain convergence. The training of the classifier can be inspected by adjusting the `verbosity` level.

If the classifier is deterministic, i.e., if it predicts a class, the value of the $R^*$ statistic is returned (algorithm 1). If the classifier is probabilistic, i.e., if it outputs probabilities of classes, the scaled Poisson-binomial distribution of the $R^*$ statistic is returned (algorithm 2).

!!! note
    The correctness of the statistic depends on the convergence of the `classifier` used internally in the statistic.


# Examples

```jldoctest rstar; setup = :(using Random; Random.seed!(101))
julia> using MLJBase, MLJIteration, EvoTrees, Statistics, StatisticalMeasures

julia> samples = fill(4.0, 100, 3, 2);
```

One can compute the distribution of the $R^*$ statistic (algorithm 2) with a probabilistic classifier. For instance, we can use a gradient-boosted trees model with `nrounds = 100` sequentially stacked trees and learning rate `eta = 0.05`:

```jldoctest rstar
julia> model = EvoTreeClassifier(; nrounds=100, eta=0.05);

julia> distribution = rstar(model, samples);

julia> round(mean(distribution); digits=2)
1.0f0
```

Note, however, that it is recommended to determine `nrounds` based on early-stopping. With the MLJ framework, this can be achieved in the following way (see the [MLJ documentation](@extref MLJ Controlling-Iterative-Models) for additional explanations):

```jldoctest rstar
julia> model = IteratedModel(;
           model=EvoTreeClassifier(; eta=0.05),
           iteration_parameter=:nrounds,
           resampling=Holdout(),
           measures=log_loss,
           controls=[Step(5), Patience(2), NumberLimit(100)],
           retrain=true,
       );

julia> distribution = rstar(model, samples);

julia> round(mean(distribution); digits=2)
1.0f0
```

For deterministic classifiers, a single $R^*$ statistic (algorithm 1) is returned. Deterministic classifiers can also be derived from probabilistic classifiers by e.g. predicting the mode. In MLJ this corresponds to a [pipeline](@extref MLJ Pipeline_MLJBase) of models.

```jldoctest rstar
julia> evotree_deterministic = Pipeline(model; operation=predict_mode);

julia> value = rstar(evotree_deterministic, samples);

julia> round(value; digits=2)
1.0
```

# References

Lambert, B., & Vehtari, A. (2020). $R^*$: A robust MCMC convergence diagnostic with uncertainty using decision tree classifiers.
