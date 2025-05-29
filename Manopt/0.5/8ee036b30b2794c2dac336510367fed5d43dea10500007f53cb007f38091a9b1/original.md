```
StopWhenSmallerOrEqual <: StoppingCriterion
```

A functor for an stopping criterion, where the algorithm if stopped when a variable is smaller than or equal to its minimum value.

# Fields

  * `value`    stores the variable which has to fall under a threshold for the algorithm to stop
  * `minValue` stores the threshold where, if the value is smaller or equal to this threshold, the algorithm stops

# Constructor

```
StopWhenSmallerOrEqual(value, minValue)
```

initialize the functor to indicate to stop after `value` is smaller than or equal to `minValue`.
