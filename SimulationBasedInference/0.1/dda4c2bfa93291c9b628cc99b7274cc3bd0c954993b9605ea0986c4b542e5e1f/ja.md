```
ensemble_kalman_analysis(
    prior::AbstractVecOrMat,
    obs::AbstractVector,
    pred::AbstractMatrix,
    alpha,
    R_cov;
    ρ_AB=1.0,
    ρ_BB=1.0,
    stochastic=true,
    dosvd=true,
    svd_thresh=0.90,
    rng::AbstractRNG=Random.GLOBAL_RNG,
)
```

単一のアンサンブルカルマン分析ステップを実行します。Kristoffer AalstadによるPython実装から適応されています：

https://github.com/ealonsogzl/MuSA/blob/0c02b8dc25a0f902bf63099de68174f4738705f0/modules/filters.py#L33
