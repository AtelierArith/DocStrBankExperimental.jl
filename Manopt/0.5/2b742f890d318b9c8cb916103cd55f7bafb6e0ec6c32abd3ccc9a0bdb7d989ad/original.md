```
get_count(ams::AbstractManoptSolverState, ::Symbol)
```

Obtain the count for a certain countable size, for example the `:Iterations`. This function returns 0 if there was nothing to count

Available symbols from within the solver state

  * `:Iterations` is passed on to the `stop` field to obtain the iteration at which the solver stopped.
