```
vals = count_unique(X)
```

Count the number of occurrences of each value in `X`.

#### Arguments

  * `X`: an iterable.

#### Return value

A `Dict{eltype(X),Int}` whose keys are the unique elements in `X` and values are their number of occurrences.

Example: the snippet

```
stats = load_stats("mystats.jld2")
for solver ∈ keys(stats)
  @info "$solver statuses" count_unique(stats[solver].status)
end
```

displays the number of occurrences of each final status for each solver in `stats`.
