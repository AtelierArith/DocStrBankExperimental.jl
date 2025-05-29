```julia
GTMFunction(; stm, name, kwargs...)

```

Returns a `DifferentialEquations`-compatible `ODEFunction` for GTM dynamics. The `stm`, and `name` keyword arguments are passed to `GTM`. All other keyword arguments are passed directly to `ODEFunction`.

# Extended Help

## Usage

Note that this `ODEFunction` output has several methods, including an in-place method! Function signatures follow `ModelingToolkit` and `DifferentialEquations` conventions.

```julia
f = GTMFunction()
let u = randn(4), p = randn(2), t = rand()
    f(u,p,t)
end
```
