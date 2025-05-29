```
all_pairs(parameters...; kwargs...)
```

Ensure that the returned test cases include every pair of parameters at least once.

# Examples

```julia
all_pairs([1, 2, 3], ["a", "b", "c"], [true, false])
```

See also: [`all_tuples`](@ref)
