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

[`StandardUpdate`](@ref) の便利なコンストラクタです。`nni_selection` は `argmax` に固定されています。このコンストラクタは、パラメータを最適化することによって最大尤度の更新を提供します。
