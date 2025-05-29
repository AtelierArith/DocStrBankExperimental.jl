```
hours(step; [start=0, labels])
```

Generates `CyclicBins` for grouping to arbitrary hour periods.  These can wrap around the end of the day.

  * `steps` the number of hours to group.

## Keywords

  * `start`: By default seasons start at `0`, but any integer `1:24` can be used.
  * `labels`: either a vector of four labels, or a function that generates labels   from `Vector{Int}` of the selected hours of the day.
