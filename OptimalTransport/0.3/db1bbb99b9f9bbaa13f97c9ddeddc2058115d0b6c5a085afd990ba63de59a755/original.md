```
sinkhorn(
    μ, ν, C, ε, alg=SinkhornGibbs();
    atol=0, rtol=atol > 0 ? 0 : √eps, check_convergence=10, maxiter=1_000,
)
```

Compute the optimal transport plan for the entropically regularized optimal transport problem with source and target marginals `μ` and `ν`, cost matrix `C` of size `(length(μ), length(ν))`, and entropic regularization parameter `ε`.

The optimal transport plan `γ` is of the same size as `C` and solves

$$
\inf_{\gamma \in \Pi(\mu, \nu)} \langle \gamma, C \rangle
+ \varepsilon \Omega(\gamma),
$$

where $\Omega(\gamma) = \sum_{i,j} \gamma_{i,j} \log \gamma_{i,j}$ is the entropic regularization term.

Every `check_convergence` steps it is assessed if the algorithm is converged by checking if the iterate of the transport plan `G` satisfies

```julia
isapprox(sum(G; dims=2), μ; atol=atol, rtol=rtol, norm=x -> norm(x, 1))
```

The default `rtol` depends on the types of `μ`, `ν`, and `C`. After `maxiter` iterations, the computation is stopped.

Batch computations for multiple histograms with a common cost matrix `C` can be performed by passing `μ` or `ν` as matrices whose columns correspond to histograms. It is required that the number of source and target marginals is equal or that a single source or single target marginal is provided (either as matrix or as vector). The optimal transport plans are returned as three-dimensional array where `γ[:, :, i]` is the optimal transport plan for the `i`th pair of source and target marginals.

See also: [`sinkhorn2`](@ref)
