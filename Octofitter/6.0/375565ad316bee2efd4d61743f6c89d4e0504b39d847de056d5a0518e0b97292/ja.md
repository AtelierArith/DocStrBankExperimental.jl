```
octofit(
    [rng::Random.AbstractRNG],
    model::Octofitter.LogDensityModel
    target_accept::Number=0.8,
    ensemble::AbstractMCMC.AbstractMCMCEnsemble=MCMCSerial();
    adaptation,
    iterations,
    drop_warmup=true,
    max_depth=12,
    initial_samples= pathfinder ? 500 : 250_000,  # 非推奨
    initial_parameters=nothing, # 非推奨
    step_size=nothing,
    verbosity=2,
)
```

`model`によって定義された事後分布からのサンプルを、AdvancedHMC.jlのNo U-Turn Samplerを使用してハミルトニアンモンテカルロで取得します。
