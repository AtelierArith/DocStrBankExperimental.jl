```julia
R2BFunction(; stm, name, kwargs...)

```

Returns an `ODEFunction` for R2B dynamics.

The order of the states follows: `[x, y, z, ẋ, ẏ, ż]`.

The order of the parameters follows: `[μ]`.

# Extended Help

### Usage

The `stm`, and `name` keyword arguments are passed to `R2B`. All other keyword arguments are passed directly to `SciMLBase.ODEFunction`.

```julia
f = R2BFunction(; stm=false, name=:R2B, jac=true)
let u = randn(6), p = randn(1), t = 0
    f(u, p, t)
end
```
