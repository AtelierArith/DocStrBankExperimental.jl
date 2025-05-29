```
Greedy(; metric = removedsize, choose = pop!)
```

Greedy contraction path solver. Greedily selects contractions that maximize a metric.

# Keywords

  * `metric` is a function that evaluates candidate pairwise tensor contractions. Defaults to [`removedsize`](@ref).
  * `choose` is a function that extracts a pairwise tensor contraction between candidates. Defaults to candidate that maximize `metric` using `pop!`.
  * `outer` If `true`, consider outer products as candidates. Defaults to `false`.

# Implementation

The implementation uses a binary heaptree to sort candidate pairwise tensor contractions. Then recursively,

1. Selects and extracts a candidate from the heaptree using the `choose` function.
2. Updates the `metric` of the candidates which contain neighbouring indices to the one selected.
3. Append the selected index to the path and go back to step 1.
