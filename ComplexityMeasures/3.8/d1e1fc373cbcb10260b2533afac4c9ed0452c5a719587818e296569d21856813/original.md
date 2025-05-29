```
MillerMadow <: DiscreteInfoEstimatorShannon
MillerMadow(measure::Shannon = Shannon())
```

The `MillerMadow` estimator is used with [`information`](@ref) to compute the discrete [`Shannon`](@ref) entropy according to [Miller1955](@citet).

# Description

The Miller-Madow estimator of Shannon entropy is given by

$$
H_S^{MM} = H_S^{plugin} + \dfrac{m - 1}{2N},
$$

where $H_S^{plugin}$ is the Shannon entropy estimated using the [`PlugIn`](@ref) estimator, `m` is the number of bins with nonzero probability (as defined in [Paninski2003](@citet)), and `N` is the number of observations.
