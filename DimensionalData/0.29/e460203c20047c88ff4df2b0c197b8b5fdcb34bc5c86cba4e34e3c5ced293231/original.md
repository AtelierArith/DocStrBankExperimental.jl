```
seasons(; [start=Dates.December, labels])
```

Generates `CyclicBins` for three month periods.

## Keywords

  * `start`: By default seasons start in December, but any integer `1:12` can be used.
  * `labels`: either a vector of four labels, or a function that generates labels from `Vector{Int}` of the selected quarters.
