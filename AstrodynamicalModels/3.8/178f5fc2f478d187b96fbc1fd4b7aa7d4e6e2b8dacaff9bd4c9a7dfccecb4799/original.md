```julia
AttitudeFunction(; stm, name, kwargs...)

```

Returns an `ODEFunction` for spacecraft attitude dynamics.

# Extended Help

### Usage

The `stm` and `name` keyword arguments are passed to `Attitude`. All other keyword arguments are passed directly to `SciMLBase.ODEFunction`.

```julia
f = AttitudeFunction()
let u = randn(7), p = randn(15), t = NaN # time invariant
    f(u, p, t)
end
```
