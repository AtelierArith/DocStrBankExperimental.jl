```
@first_stage(def)
```

Add a first stage model generation recipe to `stochasticprogram` using the syntax

```julia
@first_stage stochasticprogram::StochasticProgram = begin
    ...
end [defer]
```

where JuMP syntax is used inside the block to define the first stage model. During definition, the first stage model is referenced through the reserved keyword matching the name of `stochasticprogram`.

## Examples

The following defines the first stage model given by:

$$
  minimize 100x₁ + 150x₂
    s.t  x₁ + x₂ ≤ 120
         x₁ ≥ 40
         x₂ ≥ 20
$$

```julia
@first_stage sp = begin
    @decision(sp, x₁ >= 40)
    @decision(sp, x₂ >= 20)
    @objective(sp, Min, 100*x₁ + 150*x₂)
    @constraint(sp, x₁ + x₂ <= 120)
end
```

See also: [`@second_stage`](@ref)
