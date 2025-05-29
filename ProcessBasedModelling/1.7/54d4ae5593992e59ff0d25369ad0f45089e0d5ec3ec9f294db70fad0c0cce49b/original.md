```
ExpRelaxation(variable, expression [, τ]) <: Process
```

A common process for creating an exponential relaxation of `variable` towards the given `expression`, with timescale `τ`. It creates the equation:

```
τn*Differential(t)(variable) ~ expression - variable
```

Where `τn` is a new named `@parameter` with the value of `τ` and name `τ_($(variable))`. If instead `τ` is `nothing`, then 1 is used in its place (this is the default behavior). If `iszero(τ)`, then the equation `variable ~ expression` is created instead.

The convenience function

```julia
ExpRelaxation(process, τ)
```

allows converting an existing process (or equation) into an exponential relaxation by using the `rhs(process)` as the `expression` in the equation above.
