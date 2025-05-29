```
pairs_excursion(parameters...; kwargs...)
```

This starts with the first choice for each of the parameters. It creates test cases by varying each parameter, one at a time, through its possible values. Then it walks pairs of parameters away from the base case, and finally triples.

See also: [`all_tuples`](@ref)
