```
@stage(def)
```

Add a stage model generation recipe to `stochasticprogram` using the syntax

```julia
@stage stage stochasticprogram::StochasticProgram = begin
    @parameters param1 param2 ...
    @decision(stochasticprogram, var) ...
    @uncertain ξ
    ... JuMPdef ...
    ...
end
```

where `stage` is the stage number and JuMP syntax is used inside the block to define the stage model. During definition, the stage model is referenced using the same variable name as `stochasticprogram`.

## Examples

The following defines the first stage model given by:

$$
  minimize 100x₁ + 150x₂
    s.t  x₁ + x₂ ≤ 120
         x₁ ≥ 40
         x₂ ≥ 20
$$

and the second-stage model given by:

$$
  maximize q₁(ξ)y₁ + q₂(ξ)y₂
    s.t  6y₁ + 10y₂ ≤ 60x₁
         8y₁ + 5y₂ ≤ 60x₂
         0 ≤ y₁ ≤ d₁(ξ)
         0 ≤ y₂ ≤ d₂(ξ)
$$

where $q₁(ξ), q₂(ξ), d₁(ξ), d₂(ξ)$ depend on the scenario $ξ$ and $x₁, x₂$ are first stage variables. Two scenarios are added so that two second stage models are generated.

```jldoctest
ξ₁ = @scenario q₁ = 24.0 q₂ = 28.0 d₁ = 500.0 d₂ = 100.0 probability = 0.4
ξ₂ = @scenario q₁ = 28.0 q₂ = 32.0 d₁ = 300.0 d₂ = 300.0 probability = 0.6

sp = StochasticProgram([ξ₁, ξ₂])

@stage 1 sp = begin
    @decision(sp, x₁ >= 40)
    @decision(sp, x₂ >= 20)
    @objective(sp, Min, 100*x₁ + 150*x₂)
    @constraint(sp, x₁ + x₂ <= 120)
end

@stage 2 sp = begin
    @uncertain q₁ q₂ d₁ d₂
    @variable(sp, 0 <= y₁ <= d₁)
    @variable(sp, 0 <= y₂ <= d₂)
    @objective(sp, Max, q₁*y₁ + q₂*y₂)
    @constraint(sp, 6*y₁ + 10*y₂ <= 60*x₁)
    @constraint(sp, 8*y₁ + 5*y₂ <= 80*x₂)
end

# output

Stochastic program with:
 * 2 decision variables
 * 2 scenarios of type Scenario
Solver is default solver

```

See also: [`@parameters`](@ref), [`@decision`](@ref), [`@uncertain`](@ref)
