Create generated_quantities output files created by StanSample.jl.

```julia
stan_generate_quantities(m; ...)
stan_generate_quantities(m, id; ...)
stan_generate_quantities(m, id, chain; kwargs...)

```

### Required arguments

```julia
* `model`                    : SampleModel
```

### Optional positional arguments

```julia
* `id=1`                     : Chain id, needs to be in 1:model.num_chains
* `chain="1"                 : CSV file suffix, e.g. ...chain_1_1.csv 
```

In chain suffix `...chain_i_j`:

```julia
i : index in 1:num_julia_chains 
j : index in 1:num_cpp_chains 
```

The function checks the values of `id` and `chain`. If correct, a DataFrame is returned. Each call will return a new set of values.

See also `?available_chains`.
