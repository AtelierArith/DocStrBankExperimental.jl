```
UniformHistogram{T <: Number} <: ContinuousHistogram
```

A [`ContinuousHistogram`](@ref) with a uniform kernel for each value-error pair.

This [`ContinuousHistogram`] is formed by summing uniform kernels for each $(x_i, \epsilon_i)$ as

$$
\mathcal{H}(y) = \frac{1}{M} \sum_{i = 1}^M \mathcal{U}(y; x_i, \epsilon_i),
$$

where 

$$
\mathcal{U}(y; x_i, \epsilon_i) = \begin{cases}
\frac{1}{2\epsilon_i}, & y \in (x_i - \epsilon_i, x_i + \epsilon_i)
\\
0, & \mathrm{otherwise}
\end{cases}.
$$

These expression makes the calculation of the non-central [`moment`](@ref)s a simple mean of the  individual non-central [`moment`](@ref).

# Contents

  * `moments::Vector{T}`: a collection of moments for the `UniformHistogram` which are updated in an *online* fashion
  * `values::Vector{T}`: the values used to [`construct`](@ref) the `UniformHistogram`
  * `errors::Vector{T}`: the errors used to [`construct`](@ref) the `UniformHistogram`

!!! note
    The statistics come from calculations involving the [`moment`](@ref). The `values` and  `errors` are necessarily stored for visualization purposes.

