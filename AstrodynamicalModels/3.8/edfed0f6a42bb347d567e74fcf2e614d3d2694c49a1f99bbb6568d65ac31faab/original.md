```julia
CR3BFunction(; stm, name, kwargs...)

```

Returns an `ODEFunction` for CR3B dynamics.

The order of the states follows: `[μ]`.

The order of the parameters follows: `[μ]`.

# Extended Help

### Usage

The `stm`, and `name` keyword arguments are passed to `CR3B`. All other keyword arguments are passed directly to `SciMLBase.ODEFunction`.

```julia
f = CR3BFunction(; stm=false, jac=true)
let u = randn(6), p = randn(1), t = 0
    f(u, p, t)
end
```
