```
sinkhorn_unbalanced(μ, ν, C, λ1::Real, λ2::Real, ε; kwargs...)
```

Compute the optimal transport plan for the unbalanced entropically regularized optimal transport problem with source and target marginals `μ` and `ν`, cost matrix `C` of size `(length(μ), length(ν))`, entropic regularization parameter `ε`, and marginal relaxation terms `λ1` and `λ2`.

The optimal transport plan `γ` is of the same size as `C` and solves

$$
\inf_{\gamma} \langle \gamma, C \rangle
+ \varepsilon \Omega(\gamma)
+ \lambda_1 \operatorname{KL}(\gamma 1 | \mu)
+ \lambda_2 \operatorname{KL}(\gamma^{\mathsf{T}} 1 | \nu),
$$

where $\Omega(\gamma) = \sum_{i,j} \gamma_{i,j} \log \gamma_{i,j}$ is the entropic regularization term and $\operatorname{KL}$ is the Kullback-Leibler divergence.

The keyword arguments supported here are the same as those in the `sinkhorn_unbalanced` for unbalanced optimal transport problems with general soft marginal constraints.
