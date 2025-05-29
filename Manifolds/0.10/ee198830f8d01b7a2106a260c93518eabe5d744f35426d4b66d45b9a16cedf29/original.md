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

Estimate the covariance matrix of a set of points `x` on manifold `M`. Since the covariance matrix on a manifold is a rank 2 tensor, the function returns its coefficients in basis induced by the given tangent space basis. See Section 5 of [Pennec:2006](@cite) for details.

The mean is calculated using the specified `mean_estimation_method` using [mean](@ref Statistics.mean(::AbstractManifold, ::AbstractVector, ::AbstractApproximationMethod), and tangent vectors at this mean are calculated using the provided `inverse_retraction_method`. Finally, the covariance matrix in the tangent plane is estimated using the Euclidean space  estimator `tangent_space_covariance_estimator`. The type `CovarianceEstimator` is defined  in [`StatsBase.jl`](https://juliastats.org/StatsBase.jl/stable/cov/#StatsBase.CovarianceEstimator)  and examples of covariance estimation methods can be found in  [`CovarianceEstimation.jl`](https://github.com/mateuszbaran/CovarianceEstimation.jl/).
