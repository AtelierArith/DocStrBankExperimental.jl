```
run_diagnostics(
    meas::Vector{Float64},
    protocol::Protocol,
    model_start::BiophysicalModel,
    sampler::Sampler,
    draws::Vector{Int64},
    rng_seed::Int64=1,
    noise::Noisemodel=Noisemodel(),
)
```

異なるサンプリング長でテストされたチェーン診断を返します。この関数は、特定のモデルに対してサンプラーを最適化するのに役立ちます。

# 参考文献

Vehtari, A., Gelman, A., Simpson, D., Carpenter, B. and Bürkner, P.C., 2021. Rank-normalization, folding, and localization: An improved R ̂ for assessing convergence of MCMC (with discussion). Bayesian analysis, 16(2), pp.667-718.
