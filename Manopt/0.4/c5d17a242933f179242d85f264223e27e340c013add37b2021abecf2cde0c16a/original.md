```
StopAfterIteration <: StoppingCriterion
```

A functor for a stopping criterion to stop after a maximal number of iterations.

# Fields

  * `max_iterations`  stores the maximal iteration number where to stop at
  * `at_iteration` indicates at which iteration (including `i=0`) the stopping criterion was fulfilled and is `-1` while it is not fulfilled.

# Constructor

```
StopAfterIteration(maxIter)
```

initialize the functor to indicate to stop after `maxIter` iterations.
