```
@expectation(def)
```

Define how to form the expected scenario inside a [`@define_scenario`](@ref) block. The scenario collection is accessed through the reserved keyword `scenarios`.

```julia
@zero begin
    ...
    return zero_scenario
end
```

## Examples

The following defines expectation for the example scenario defined in [`@scenario`](@ref)

```julia
@expectation begin
    return ExampleScenario(sum([probability(s)*s.ξ for s in scenarios]))
end
```

See also [`@define_scenario`](@ref)
