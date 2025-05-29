```julia
PlanarEntryFunction(; name, kwargs...)

```

Returns an `ODEFunction` for Planar Entry dynamics. Results are cached with `Memoize.jl`.

The order of the states follows: `[γ, v, r, θ]`.

The order of the parameters follows: `[R, P, H, m, A, C, μ]`

# Extended Help

### Usage

The `name` keyword argument is ]passed to `PlanarEntry`. All other keyword arguments are passed directly to `SciMLBase.ODEFunction`.

```julia
f = PlanarEntryFunction()
let u = randn(4), p = randn(7), t = NaN # time invariant
    f(u, p, t)
end
```
