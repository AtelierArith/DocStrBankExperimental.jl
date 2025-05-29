```
@ode_def name begin
    differential equation
end parameters :: ODEFunction
```

## Definition of the Domain-Specific Language (DSL)

A helper macro is provided to make it easier to define a `ParameterizedFunction`, and it will symbolically compute a bunch of extra functions to make the differential equation solvers run faster. For example, to define the previous `LotkaVolterra`, you can use the following command:

```julia
f = @ode_def LotkaVolterra begin
    dx = a * x - b * x * y
    dy = -c * y + d * x * y
end a b c d
```

or you can define it anonymously:

```julia
f = @ode_def begin
    dx = a * x - b * x * y
    dy = -c * y + d * x * y
end a b c d
```

`@ode_def` uses ModelingToolkit.jl internally and returns an `ODEFunction` with the extra definitions (Jacobian, parameter Jacobian, etc.) defined through the MTK symbolic tools.
