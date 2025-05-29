```
ot_plan(::SqEuclidean, μ::MvNormal, ν::MvNormal)
```

Compute the optimal transport plan for the Monge-Kantorovich problem with multivariate normal distributions `μ` and `ν` as source and target marginals and cost function $c(x, y) = \|x - y\|_2^2$.

In this setting, for $\mu = \mathcal{N}(m_\mu, \Sigma_\mu)$ and $\nu = \mathcal{N}(m_\nu, \Sigma_\nu)$, the optimal transport plan is the Monge map

$$
T \colon x \mapsto m_\nu
+ \Sigma_\mu^{-1/2}
{\big(\Sigma_\mu^{1/2} \Sigma_\nu \Sigma_\mu^{1/2}\big)}^{1/2}\Sigma_\mu^{-1/2}
(x - m_\mu).
$$

See also: [`ot_cost`](@ref), [`emd`](@ref)
