```
@uncertain(def)
```

In a @stage block, annotate each uncertain variable using the syntax

```julia
@uncertain var1, var2, ...
```

or using JuMP's container syntax

```julia
@uncertain ξ[i=..., j=..., ...]
```

This assumes that the [`Scenario`] type is used. Matching scenario data is then conveniently created using [`@scenario`](@ref).

Alternatively, user-defined scenarios can be specified by annotating the type. Also, inside a @stochastic*model block, user-defined scenarios can be created during the @uncertain annotation, using [`@define*scenario`](@ref) syntax.

## Examples

The following are equivalent ways of declaring a random vector $[q₁(ξ) q₂(ξ) d₁(ξ) d₂(ξ)]$ in a `@stage` block, and creating a matching scenario instance of probability $0.4$ and values $[24.0 28.0 500.0 100.0]$.ö

```julia
@uncertain q₁ q₂ d₁ d₂
ξ₁ = @scenario q₁ = 24.0 q₂ = 28.0 d₁ = 500.0 d₂ = 100.0 probability = 0.4

@uncertain ξ[i in 1:4]
ξ₁ = @scenario ξ[i in 1:4] = [24.0, 28.0, 500.0, 100.0] probability = 0.4

@define_scenario SimpleScenario = begin
    q₁::Float64
    q₂::Float64
    d₁::Float64
    d₂::Float64
end
@uncertain ξ::SimpleScenario
ξ₁ = SimpleScenario(24.0, 28.0, 500.0, 100.0, probability = 0.4)

@stochastic_model begin
    ...
    @uncertain ξ::SimpleScenario = begin
        q₁::Float64
        q₂::Float64
        d₁::Float64
        d₂::Float64
    end
    ...
end
ξ₁ = SimpleScenario(24.0, 28.0, 500.0, 100.0 probability = 0.4)
```

See also [`@scenario`](@ref), [`@define_scenario`](@ref), [`@parameters`](@ref), [`@decision`](@ref), [`@stage`](@ref)
