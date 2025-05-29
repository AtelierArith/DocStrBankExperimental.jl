```
@zero(def)
```

Define the additive zero scenario inside a @scenario block using the syntax:

```julia
@zero begin
    ...
    return zero_scenario
end
```

## Examples

The following defines a zero scenario for the example scenario defined in [`@define_scenario`](@ref)

```julia
@zero begin
    return ExampleScenario(0.0)
end
```

See also [`@define_scenario`](@ref)
