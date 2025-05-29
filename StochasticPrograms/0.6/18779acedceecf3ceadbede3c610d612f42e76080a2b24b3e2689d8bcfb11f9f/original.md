```
has_duals(stochasticprogram::StochasticProgram; result::Int = 1)
```

Return `true` if the solver has a primal solution in the first-stage of `stochasticprogram` in result index `result` available to query, otherwise return `false`.
