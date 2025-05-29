```
ess_rhat(
    samples::AbstractArray{<:Union{Missing,Real}};
    kind::Symbol=:rank,
    kwargs...,
) -> NamedTuple{(:ess, :rhat)}
```

Estimate the effective sample size and $\widehat{R}$ of the `samples` of shape `(draws, [chains[, parameters...]])`.

When both ESS and $\widehat{R}$ are needed, this method is often more efficient than calling `ess` and `rhat` separately.

See [`rhat`](@ref) for a description of supported `kind`s and [`ess`](@ref) for a description of `kwargs`.
