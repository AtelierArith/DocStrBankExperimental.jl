```
ot_cost(::SqEuclidean, μ::MvNormal, ν::MvNormal)
```

Compute the squared 2-Wasserstein distance between normal distributions `μ` and `ν` as source and target marginals.

In this setting, the optimal transport cost can be computed as

$$
W_2^2(\mu, \nu) = \|m_\mu - m_\nu \|^2 + \mathcal{B}(\Sigma_\mu, \Sigma_\nu)^2,
$$

where $\mu = \mathcal{N}(m_\mu, \Sigma_\mu)$, $\nu = \mathcal{N}(m_\nu, \Sigma_\nu)$, and $\mathcal{B}$ is the Bures metric.

See also: [`ot_plan`](@ref), [`emd2`](@ref)
