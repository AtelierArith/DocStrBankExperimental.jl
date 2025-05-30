```
@scalar_rule(f(x₁, x₂, ...),
             @setup(statement₁, statement₂, ...),
             (∂f₁_∂x₁, ∂f₁_∂x₂, ...),
             (∂f₂_∂x₁, ∂f₂_∂x₂, ...),
             ...)
```

A convenience macro that generates simple scalar forward or reverse rules using the provided partial derivatives. Specifically, generates the corresponding methods for `frule` and `rrule`:

```julia
function ChainRulesCore.frule((NoTangent(), Δx₁, Δx₂, ...), ::typeof(f), x₁::Number, x₂::Number, ...)
    Ω = f(x₁, x₂, ...)
    $(statement₁, statement₂, ...)
    return Ω, (
            (∂f₁_∂x₁ * Δx₁ + ∂f₁_∂x₂ * Δx₂ + ...),
            (∂f₂_∂x₁ * Δx₁ + ∂f₂_∂x₂ * Δx₂ + ...),
            ...
        )
end

function ChainRulesCore.rrule(::typeof(f), x₁::Number, x₂::Number, ...)
    Ω = f(x₁, x₂, ...)
    $(statement₁, statement₂, ...)
    return Ω, ((ΔΩ₁, ΔΩ₂, ...)) -> (
            NoTangent(),
            ∂f₁_∂x₁ * ΔΩ₁ + ∂f₂_∂x₁ * ΔΩ₂ + ...),
            ∂f₁_∂x₂ * ΔΩ₁ + ∂f₂_∂x₂ * ΔΩ₂ + ...),
            ...
        )
end
```

If no type constraints in `f(x₁, x₂, ...)` within the call to `@scalar_rule` are provided, each parameter in the resulting `frule`/`rrule` definition is given a type constraint of `Number`. Constraints may also be explicitly be provided to override the `Number` constraint, e.g. `f(x₁::Complex, x₂)`, which will constrain `x₁` to `Complex` and `x₂` to `Number`.

At present this does not support defining for closures/functors. Thus in reverse-mode, the first returned partial, representing the derivative with respect to the function itself, is always `NoTangent()`. And in forward-mode, the first input to the returned propagator is always ignored.

The result of `f(x₁, x₂, ...)` is automatically bound to `Ω`. This allows the primal result to be conveniently referenced (as `Ω`) within the derivative/setup expressions.

This macro assumes complex functions are holomorphic. In general, for non-holomorphic functions, the `frule` and `rrule` must be defined manually.

If the derivative is one, (e.g. for identity functions) `true` can be used as the most general multiplicative identity.

The `@setup` argument can be elided if no setup code is need. In other words:

```julia
@scalar_rule(f(x₁, x₂, ...),
             (∂f₁_∂x₁, ∂f₁_∂x₂, ...),
             (∂f₂_∂x₁, ∂f₂_∂x₂, ...),
             ...)
```

is equivalent to:

```julia
@scalar_rule(f(x₁, x₂, ...),
             @setup(nothing),
             (∂f₁_∂x₁, ∂f₁_∂x₂, ...),
             (∂f₂_∂x₁, ∂f₂_∂x₂, ...),
             ...)
```

For examples, see ChainRules' `rulesets` directory.

See also: [`frule`](@ref), [`rrule`](@ref).
