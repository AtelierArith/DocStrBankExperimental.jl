Compute the quadratic approximation to the posterior distribution.

```julia
stan_quap(name, model; kwargs...)

```

### Required arguments

```julia
* `name::String`                : Name for SampleModel
* `model::String`               : Stan Language model
```

### Keyword arguments

```julia
* `data`                        : Data for model (NamedTuple or Duct)
* `init`                        : Initial values for parameters (NamedTuple or Dict)
```

### Reyrns

```julia
* `res::QuapResult`              : Returned object
```

In general using `init` results in better behavior.
