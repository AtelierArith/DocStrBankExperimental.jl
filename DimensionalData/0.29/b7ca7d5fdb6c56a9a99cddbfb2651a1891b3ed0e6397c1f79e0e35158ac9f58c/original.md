```
months(step; [start=Dates.January, labels])
```

Generates `CyclicBins` for grouping to arbitrary month periods.  These can wrap around the end of a year.

  * `step` the number of months to group.

## Keywords

  * `start`: By default months start in January, but any integer `1:12` can be used.
  * `labels`: either a vector of labels matching the number of groups,    or a function that generates labels from `Vector{Int}` of the selected months.
