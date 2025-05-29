```
sample(
    rng::AbstractRNG,
    sampler::MCHMCSampler,
    target::Target,
    n::Int;
    init_params = nothing,
    fol_name = ".",
    file_name = "samples",
    progress = true,
    kwargs...
)
```

サンプリングルーチン
