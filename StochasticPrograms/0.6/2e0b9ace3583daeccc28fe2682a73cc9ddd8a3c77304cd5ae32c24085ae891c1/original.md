```
@sampler(def)
```

Define a sampler type for some `scenariotype` compatible with StochasticPrograms using the syntax

```julia
@sampler samplername = begin
    ...internals...

    @sample scenariotype begin
        ...
        return scenario
    end
end
```

Any internal state required by the sampler, as well as any specialized constructor, are defined in the @sampler block as they would be in any Julia struct. Define the sample operation inside the [`@sample`](@ref) block and specify the `scenariotype` that the sampler returns. The defined sampler will be available on all Julia processes.

## Examples

The following defines a simple dummy sampler, with some internal weight value, for the scenario defined in [`@scenario`](@ref), and samples one scenario.

```jldoctest; setup = :(@scenario ExampleScenario = ξ::Float64), filter = r".*"
@sampler ExampleSampler = begin
    w::Float64

    ExampleSampler(w::AbstractFloat) = new(w)

    @sample ExampleScenario begin
        @parameters w
        return ExampleScenario(w*randn(), probability = rand())
    end
end
s = ExampleSampler(2.0)
s()

# output

ExampleScenario with probability 0.29
  ξ: 1.48


```

See also: [`@sample`](@ref), [`@scenario`](@ref)
