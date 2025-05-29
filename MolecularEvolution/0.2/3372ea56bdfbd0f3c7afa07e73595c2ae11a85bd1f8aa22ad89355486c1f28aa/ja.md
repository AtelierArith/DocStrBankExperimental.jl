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

[`StandardUpdate`](@ref) の便利なコンストラクタです。`nni_selection` は `softmax_sampler` に固定されています。このコンストラクタは、事後分布からサンプリングすることによってベイズ更新を提供します。
