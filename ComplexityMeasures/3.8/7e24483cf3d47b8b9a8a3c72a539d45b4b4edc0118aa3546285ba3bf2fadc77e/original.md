```
Counts <: Array{<:Integer, N}
Counts(counts [, outcomes [, dimlabels]]) → c
```

`Counts` stores an `N`-dimensional array of integer `counts` corresponding to a set of `outcomes`. This is typically called a "frequency table" or ["contingency table"](https://en.wikipedia.org/wiki/Contingency_table).

If `c isa Counts`, then `c.outcomes[i]` is an abstract vector containing the outcomes along the `i`-th dimension, where `c[i][j]` is the count corresponding to the outcome `c.outcomes[i][j]`, and `c.dimlabels[i]` is the label of the `i`-th dimension. Both labels and outcomes are assigned automatically if not given. `c` itself can be manipulated and iterated over like its stored array.
