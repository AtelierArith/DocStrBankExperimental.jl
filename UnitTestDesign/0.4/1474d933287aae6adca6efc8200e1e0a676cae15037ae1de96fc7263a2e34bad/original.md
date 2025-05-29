```
values_excursion(parameters...; kwargs...)
```

This starts with the first choice for each of the parameters. It creates test cases by varying each parameter, one at a time, through its possible values.

# Examples

```julia
values_excursion([:a, :b, :c], [1, 2, 3])
```

See also: [`all_tuples`](@ref)
