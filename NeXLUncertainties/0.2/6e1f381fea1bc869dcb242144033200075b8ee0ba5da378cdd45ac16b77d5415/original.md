```
parallel(mm1::MeasurementModel, models::MeasurementModel...)
```

Implements a mechanism to combine `MeasurementModel`s that work on the same input to produce output that is the combination of the outputs of all the measurement models.  This is useful when a calculation forks into 2 or more distinct calculations which are later composed as is shown in the examples.

Examples:

```
j = parallel(f,g) # Creates a ParallelMeasurementModel([f,g], true)
y = j(x) # where y combines the outputs of f(x) and h(x)
z = parallel(f, g, h)(x) # Conceptually like combine(f(x), g(x), h(x)) into a single output
(k ∘ parallel(f, g, h))(x) == k(z) # Conceptually like k(f(x),g(x),h(x))
```
