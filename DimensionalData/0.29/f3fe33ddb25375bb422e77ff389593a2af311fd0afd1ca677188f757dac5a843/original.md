```
CyclicBins(f; cycle, start, step, labels)
```

Cyclic bins to reduce groups after applying function `f`. Groups can wrap around the cycle. This is used for grouping in [`seasons`](@ref), [`months`](@ref) and [`hours`](@ref) but can also be used for custom cycles.

  * `f`: a grouping function of the lookup values, by default `identity`.

## Keywords

  * `cycle`: the length of the cycle, in return values of `f`.
  * `start`: the start of the cycle: a return value of `f`.
  * `step` the number of sequential values to group.
  * `labels`: either a vector of labels matching the number of groups,    or a function that generates labels from `Vector{Int}` of the selected bins.

When the return value of `f` is a tuple, binning is applied to the *last* value of the tuples.
