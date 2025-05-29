```
GaussianHistogram{T <: Number} <: ContinuousHistogram
```

A [`ContinuousHistogram`](@ref) with a Gaussian kernel for each value-error pair.

This [`ContinuousHistogram`] is formed by summing Gaussian kernels for each $(\mu_i, \sigma_i)$ as

$$
\mathcal{H}(y) = \frac{1}{M} \sum_{i = 1}^M G(y; \mu_i, \sigma_i),
$$

where 

$$
G(y; \mu_i, \sigma_i) = \frac{ \exp\left[ -\frac{ \left( y - \mu_i \right)^2 }{2 \sigma_i^2} \right] }{ \sigma_i \sqrt{2\pi}}.
$$

This expression makes the calculation of the non-central [`moment`](@ref) a simple mean of the  individual non-central [`moment`](@ref).

# Contents

  * `moments::Vector{T}`: a collection of moments for the `GaussianHistogram` which are updated in an *online* fashion
  * `values::Vector{T}`: the values used to [`construct`](@ref) the `GaussianHistogram`
  * `errors::Vector{T}`: the errors used to [`construct`](@ref) the `GaussianHistogram`

!!! note
    The statistics come from calculations involving the [`moment`](@ref). The `values` and  `errors` are necessarily stored for visualization purposes.

