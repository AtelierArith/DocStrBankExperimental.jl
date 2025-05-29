```
update(phd::PHDFilter, b0::GaussianMixture, Z::Vector{AbstractVector},
	T::Real, U::Real, J_max::Integer)
```

Perform an update step using a GMPHD Filter.

Arguments:

  * `phd::PHDFilter` PHD filter to step through. [PHD Filter]
  * `b0::GaussianMixture` Prior state distribution. [Gaussian Mixture]
  * `Z::Matrix` Matrix of measurements. [Measurements]
  * `T::Real` Truncation threshold.  Drop distributions with weight less than T
  * `U::Real` Merging threshold.  Merge if (μ*1-μ*2)^T * Σ^-1 * (μ*1-μ*2) < U
  * `J_max::Integer` Maximum number of features

Returns:

  * `bn::GaussianMixture` Describe first return value. [Gaussian Mixture]

References:

1. Vo, B. N., & Ma, W. K. (2006). The Gaussian mixture probability hypothesis

density filter. IEEE Transactions on signal processing, 54(11), 4091-4104.
