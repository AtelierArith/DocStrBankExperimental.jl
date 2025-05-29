```
pairs_excursion(parameters...; kwargs...)
```

This starts with the first choice for each of the parameters. It creates test cases by varying each parameter, one at a time, through its possible values. Then it walks pairs of parameters away from the base case.

# Examples

```julia
pairs_excursion([:a, :b], [1, 2], [1, 2], ["a", "b"])
```

See also: [`all_tuples`](@ref)
