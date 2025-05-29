```
@define_scenario(def)
```

Define a scenario type compatible with StochasticPrograms using the syntax

```julia
@define_scenario name = begin
    ...structdef...

    [@zero begin
        ...
        return zero(scenario)
    end]

    [@expectation begin
        ...
        return expected(scenarios)
     end]
end
```

The generated type is referenced through `name` and a default constructor is always generated. This constructor accepts the keyword `probability` to set the probability of the scenario occuring. Otherwise, any internal variables and specialized constructors are defined in the @define_scenario block as they would be in any Julia struct.

If possible, a `zero` method and an `expected` method will be generated for the defined type. Otherwise, or if the default implementation is not desired, these can be user provided through [`@zero`](@ref) and [`@expectation`](@ref).

The defined scenario type will be available on all Julia processes.

## Examples

The following defines a simple scenario $ξ$ with a single value.

```jldoctest
@define_scenario ExampleScenario = begin
    ξ::Float64
end

ExampleScenario(1.0, probability = 0.5)

# output

ExampleScenario with probability 0.5
  ξ: 1.0

```

See also: [`@zero`](@ref), [`@expectation`](@ref), [`@sampler`](@ref)
