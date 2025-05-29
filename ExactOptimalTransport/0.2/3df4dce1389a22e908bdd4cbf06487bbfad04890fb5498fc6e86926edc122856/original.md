```
ot_plan(c, μ, ν; kwargs...)
```

Compute the optimal transport plan for the Monge-Kantorovich problem with source and target marginals `μ` and `ν` and cost `c`.

The optimal transport plan solves

$$
\inf_{\gamma \in \Pi(\mu, \nu)} \int c(x, y) \, \mathrm{d}\gamma(x, y)
$$

where $\Pi(\mu, \nu)$ denotes the couplings of $\mu$ and $\nu$.

See also: [`ot_cost`](@ref)
