```
@stochastic_model(def)
```

Define a stochastic model capable of instantiating stochastic programs, using the syntax

```julia
@stochastic_model model_name begin
    ...
    @stage x begin
      ...
    end
    ...
end
```

where the inner blocks are [`@stage`](@ref) blocks. At least two stages must be specified in consecutive order. A stochastic model object can later be used to [`instantiate`](@ref) stochastic programs using a given set of scenarios or by using samplers. The model is referenced using `model_name` in the [`@stage`](@ref) blocks. If `model_name` is left out, the macro returns an anonymous model object, and the reserved keyword `model` must be used in the [`@stage`](@ref) blocks. Otherwise, the resulting stochastic model object is stored in a variable named `model_name`.

## Examples

The following defines a stochastic model consisitng of the first stage model given by:

$$
  minimize 100x₁ + 150x₂
    s.t  x₁ + x₂ ≤ 120
         x₁ ≥ 40
         x₂ ≥ 20
$$

and the second-stage model given by:

$$
  minimize q₁(ξ)y₁ + q₂(ξ)y₂
    s.t  6y₁ + 10y₂ ≤ 60x₁
         8y₁ + 5y₂ ≤ 60x₂
         0 ≤ y₁ ≤ d₁(ξ)
         0 ≤ y₂ ≤ d₂(ξ)
$$

where $q₁(ξ), q₂(ξ), d₁(ξ), d₂(ξ)$ depend on the scenario $ξ$.

```julia
@stochastic_model sm begin
    @stage 1 begin
        @decision(sm, x₁ >= 40)
        @decision(sm, x₂ >= 20)
        @objective(sm, Min, 100*x₁ + 150*x₂)
        @constraint(sm, x₁ + x₂ <= 120)
    end
    @stage 2 begin
        @uncertain q₁ q₂ d₁ d₂
        @variable(sm, 0 <= y₁ <= d₁)
        @variable(sm, 0 <= y₂ <= d₂)
        @objective(sm, Min, q₁*y₁ + q₂*y₂)
        @constraint(sm, 6*y₁ + 10*y₂ <= 60*x₁)
        @constraint(sm, 8*y₁ + 5*y₂ <= 80*x₂)
    end
end
```

or alternatively using anonymous syntax:

```julia
sm = @stochastic_model begin
    @stage 1 begin
        @decision(model, x₁ >= 40)
        @decision(model, x₂ >= 20)
        @objective(model, Min, 100*x₁ + 150*x₂)
        @constraint(model, x₁ + x₂ <= 120)
    end
    @stage 2 begin
        @uncertain q₁ q₂ d₁ d₂
        @variable(model, 0 <= y₁ <= d₁)
        @variable(model, 0 <= y₂ <= d₂)
        @objective(model, Min, q₁*y₁ + q₂*y₂)
        @constraint(model, 6*y₁ + 10*y₂ <= 60*x₁)
        @constraint(model, 8*y₁ + 5*y₂ <= 80*x₂)
    end
end
```

where the reserved keyword `model` is used throughout.

See also: [`@stage`](@ref), [`@parameters`](@ref), [`@decision`](@ref), [`@uncertain`](@ref)
