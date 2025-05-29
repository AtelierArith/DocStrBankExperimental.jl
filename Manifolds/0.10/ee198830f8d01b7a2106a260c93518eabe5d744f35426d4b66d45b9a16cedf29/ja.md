```
Statistics.cov(
    M::AbstractManifold,
    x::AbstractVector;
    basis::AbstractBasis=DefaultOrthonormalBasis(),
    tangent_space_covariance_estimator::CovarianceEstimator=SimpleCovariance(;
        corrected=true,
    ),
    mean_estimation_method::AbstractApproximationMethod=GradientDescentEstimation(),
    inverse_retraction_method::AbstractInverseRetractionMethod=default_inverse_retraction_method(
        M, eltype(x),
    ),
)
```

多様体 `M` 上の点の集合 `x` の共分散行列を推定します。多様体上の共分散行列はランク2のテンソルであるため、この関数は与えられた接空間基底によって誘導される基底におけるその係数を返します。詳細については、[Pennec:2006](@cite) のセクション5を参照してください。

平均は指定された `mean_estimation_method` を使用して計算され、[mean](@ref Statistics.mean(::AbstractManifold, ::AbstractVector, ::AbstractApproximationMethod) によってこの平均での接ベクトルが提供された `inverse_retraction_method` を使用して計算されます。最後に、接平面における共分散行列はユークリッド空間推定器 `tangent_space_covariance_estimator` を使用して推定されます。型 `CovarianceEstimator` は [`StatsBase.jl`](https://juliastats.org/StatsBase.jl/stable/cov/#StatsBase.CovarianceEstimator) で定義されており、共分散推定方法の例は [`CovarianceEstimation.jl`](https://github.com/mateuszbaran/CovarianceEstimation.jl/) で見つけることができます。
