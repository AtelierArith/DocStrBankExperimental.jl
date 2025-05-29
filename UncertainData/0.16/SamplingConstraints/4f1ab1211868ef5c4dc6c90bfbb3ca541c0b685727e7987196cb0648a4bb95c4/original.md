```
truncate(population::AbstractScalarPopulation, constraint::NoConstraint)
```

Get the elements and the associated sampling weights of the `population` members  satisfying the sampling `constraint`.

  * If `constraint` is a `NoConstraint` instance, then all members and weights are    returned unmodified.
