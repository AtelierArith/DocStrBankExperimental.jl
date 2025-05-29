```
sinkhorn_barycenter(μ, C, ε, w, alg = SinkhornGibbs(); kwargs...)
```

Compute the Sinkhorn barycenter for a collection of `N` histograms contained in the columns of `μ`, for a cost matrix `C` of size `(size(μ, 1), size(μ, 1))`, relative weights `w` of size `N`, and entropic regularisation parameter `ε`. Returns the entropically regularised barycenter of the `μ`, i.e. the histogram `ρ` of length `size(μ, 1)` that solves

$$
\min_{\rho \in \Sigma} \sum_{i = 1}^N w_i \operatorname{OT}_{\varepsilon}(\mu_i, \rho)
$$

where $\operatorname{OT}_{ε}(\mu, \nu) = \inf_{\gamma \Pi(\mu, \nu)} \langle \gamma, C \rangle + \varepsilon \Omega(\gamma)$ is the entropic optimal transport loss with cost $C$ and regularisation $\epsilon$.
