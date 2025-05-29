```
MetricHeuristic(metric, fluents[, coeffs])
```

Heuristic that computes a `metric` distance between the current state and the  goals for the specified numeric `fluents`, which are (optionally) multiplied by scalar `coeffs` before metric computation.

This heuristic can only be used with goal formulae that contain a list of  equality constraints for the provided `fluents`.

# Arguments

  * `metric`

    Function that returns a scalar value given a vector of differences between the fluent values for the current state and the goal.
  * `fluents`

    A list of `Term`s that refer to numeric fluents in the state.
  * `coeffs`

    A list of scalar coefficients which each fluent value will be multiplied  by before metric computation. Defaults to `1` for all fluents.
