```
BayesUpdate(;
    nni = 1,
    branchlength = 1,
    root = 0,
    models = 0,
    refresh = false,
    branchlength_sampler::UnivariateSampler = BranchlengthSampler(
        Normal(0, 2),
        Normal(-1, 1),
    ),
    root_sampler::RootSample = StandardRootSample(1.0, 1),
    models_sampler::ModelsUpdate = StandardModelsUpdate()
)
```

Convenience constructor for [`StandardUpdate`](@ref). The `nni_selection` is fixed to `softmax_sampler`.  This constructor provides Bayesian updates by sampling from the posterior distribution.
