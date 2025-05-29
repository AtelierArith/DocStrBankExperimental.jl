```
bounded(val::Real, lower_bound::Real, upper_bound::Real)
```

Constructs a `Bounded`. The `value` of a `Bounded` is a `Real` number that is constrained to be within the interval (`lower_bound`, `upper_bound`), and is equal to `val`. This is represented internally in terms of an `unconstrained_value` and a `transform` that maps any `Real` to this interval.
