```
StopWhenLagrangeMultiplierLess <: StoppingCriterion
```

Stopping Criteria for Lagrange multipliers.

Currently these are meant for the [`convex_bundle_method`](@ref) and [`proximal_bundle_method`](@ref), where based on the Lagrange multipliers an approximate (sub)gradient $g$ and an error estimate $ε$ is computed.

The `mode=:both` requires that both $ε$ and $\lvert g \rvert$ are smaller than their `tolerance`s for the [`convex_bundle_method`](@ref), and that $c$ and $\lvert d \rvert$ are smaller than their `tolerance`s for the [`proximal_bundle_method`](@ref).

The `mode=:estimate` requires that, for the [`convex_bundle_method`](@ref) $-ξ = \lvert g \rvert^2 + ε$ is less than a given `tolerance`. For the [`proximal_bundle_method`](@ref), the equation reads $-ν = μ \lvert d \rvert^2 + c$.

# Constructors

```
StopWhenLagrangeMultiplierLess(tolerance=1e-6; mode::Symbol=:estimate, names=nothing)
```

Create the stopping criterion for one of the `mode`s mentioned. Note that tolerance can be a single number for the `:estimate` case, but a vector of two values is required for the `:both` mode. Here the first entry specifies the tolerance for $ε$ ($c$), the second the tolerance for $\lvert g \rvert$ ($\lvert d \rvert$), respectively.
