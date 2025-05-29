```
sinkhorn_unbalanced2(μ, ν, C, λ1, λ2, ε; plan=nothing, kwargs...)
sinkhorn_unbalanced2(μ, ν, C, proxdivF1!, proxdivF2!, ε; plan=nothing, kwargs...)
```

Compute the optimal transport plan for the unbalanced entropically regularized optimal transport problem with source and target marginals `μ` and `ν`, cost matrix `C` of size `(length(μ), length(ν))`, entropic regularization parameter `ε`, and marginal relaxation terms `λ1` and `λ2` or soft marginal constraints with "proxdiv" functions `proxdivF1!` and `proxdivF2!`.

A pre-computed optimal transport `plan` may be provided. The other keyword arguments supported here are the same as those in the [`sinkhorn_unbalanced`](@ref) for unbalanced optimal transport problems with general soft marginal constraints.

See also: [`sinkhorn_unbalanced`](@ref)
