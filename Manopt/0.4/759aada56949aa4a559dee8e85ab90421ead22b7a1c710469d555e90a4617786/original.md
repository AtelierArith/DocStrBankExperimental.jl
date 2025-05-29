```
StopAfter <: StoppingCriterion
```

store a threshold when to stop looking at the complete runtime. It uses `time_ns()` to measure the time and you provide a `Period` as a time limit, for example `Minute(15)`.

# Fields

  * `threshold` stores the `Period` after which to stop
  * `start` stores the starting time when the algorithm is started, that is a call with `i=0`.
  * `time` stores the elapsed time
  * `at_iteration` indicates at which iteration (including `i=0`) the stopping criterion was fulfilled and is `-1` while it is not fulfilled.

# Constructor

```
StopAfter(t)
```

initialize the stopping criterion to a `Period t` to stop after.
