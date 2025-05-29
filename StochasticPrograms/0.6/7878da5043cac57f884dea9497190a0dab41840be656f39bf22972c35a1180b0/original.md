```
@second_stage(def)
```

Add a second stage model generation recipe to `stochasticprogram` using the syntax

```julia
@second_stage stochasticprogram::StochasticProgram = begin
    @known var1 var2 ...
    ...
end
```

where JuMP syntax is used inside the block to define the second stage model. During definition, the second stage model is referenced through the reserved keyword matching the name of `stochasticprogram`.

## Examples

The following defines the second stage model given by:

$$
  minimize q₁(ξ)y₁ + q₂(ξ)y₂
    s.t  6y₁ + 10y₂ ≤ 60x₁
         8y₁ + 5y₂ ≤ 60x₂
         0 ≤ y₁ ≤ d₁(ξ)
         0 ≤ y₂ ≤ d₂(ξ)
$$

where $q₁(ξ), q₂(ξ), d₁(ξ), d₂(ξ)$ depend on the scenario $ξ$ and $x₁, x₂$ are first stage variables. Two scenarios are added so that two second stage models are generated.

```julia
@second_stage sp = begin
    @known(sp, x₁, x₂)
    @uncertain q₁ q₂ d₁ d₂
    @variable(sp, 0 <= y₁ <= d₁)
    @variable(sp, 0 <= y₂ <= d₂)
    @objective(sp, Min, q₁*y₁ + q₂*y₂)
    @constraint(sp, 6*y₁ + 10*y₂ <= 60*x₁)
    @constraint(sp, 8*y₁ + 5*y₂ <= 80*x₂)
end
```

See also: [`@first_stage`](@ref)
