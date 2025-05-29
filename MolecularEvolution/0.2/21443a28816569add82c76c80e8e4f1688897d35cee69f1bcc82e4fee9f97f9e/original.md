```
MaxLikUpdate(;
    nni = 1,
    branchlength = 1,
    root = 0,
    models = 0,
    refresh = false,
    branchlength_optimizer::UnivariateOpt = GoldenSectionOpt(),
    root_optimizer = StandardRootOpt(10),
    models_optimizer::ModelUpdate = StandardModelUpdate()
)
```

Convenience constructor for [`StandardUpdate`](@ref). The `nni_selection` is fixed to `argmax`. This constructor provides Maximum Likelihood updates by optimizing parameters.
