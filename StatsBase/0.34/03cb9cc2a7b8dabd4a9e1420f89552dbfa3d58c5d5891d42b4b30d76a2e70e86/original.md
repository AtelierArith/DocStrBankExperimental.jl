```
quantile(v, w::AbstractWeights, p)
```

Compute the weighted quantiles of a vector `v` at a specified set of probability values `p`, using weights given by a weight vector `w` (of type `AbstractWeights`). Weights must not be negative. The weights and data vectors must have the same length. `NaN` is returned if `x` contains any `NaN` values. An error is raised if `w` contains any `NaN` values.

With [`FrequencyWeights`](@ref), the function returns the same result as `quantile` for a vector with repeated values. Weights must be integers.

With non `FrequencyWeights`,  denote $N$ the length of the vector, $w$ the vector of weights, $h = p (\sum_{i ≤ N} w_i - w_1) + w_1$ the cumulative weight corresponding to the probability $p$ and $S_k = \sum_{i \leq k} w_i$ the cumulative weight for each observation, define $v_{k+1}$ the smallest element of `v` such that $S_{k+1}$ is strictly superior to $h$. The weighted $p$ quantile is given by $v_k + γ (v_{k+1} - v_k)$ with $γ = (h - S_k)/(S_{k+1} - S_k)$. In particular, when all weights are equal, the function returns the same result as the unweighted `quantile`.
