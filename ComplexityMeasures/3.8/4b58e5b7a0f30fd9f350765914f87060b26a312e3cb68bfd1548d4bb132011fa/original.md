```
PlugIn(e::InformationMeasure) <: DiscreteInfoEstimatorGeneric
```

The `PlugIn` estimator is also called the empirical/naive/"maximum likelihood" estimator, and is used with [`information`](@ref) to any discrete [`InformationMeasure`](@ref).

It computes any quantity exactly as given by its formula. When computing an information measure, which here is defined as a probabilities functional, it computes the quantity directly from a probability mass function, which is derived from maximum-likelihood ([`RelativeAmount`](@ref) estimates of the probabilities.

## Bias of plug-in estimates

The plugin-estimator of [`Shannon`](@ref) entropy underestimates the true entropy, with a bias that grows with the number of distinct [`outcomes`](@ref) (Arora et al., 2022)[Arora2022](@cite),

$$
bias(H_S^{plugin}) = -\dfrac{K-1}{2N} + o(N^-1).
$$

where `K` is the number of distinct outcomes, and `N` is the sample size. Many authors have tried to remedy this by proposing alternative Shannon entropy estimators. For example, the [`MillerMadow`](@ref) estimator is a simple correction to the plug-in estimator that adds back the bias term above. Many other estimators exist; see [`DiscreteInfoEstimator`](@ref)s for an overview.
