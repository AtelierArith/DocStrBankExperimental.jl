```
abstract type IntervalClass <: Interval end
```

Any interval class type should be a subtype of `IntervalClass`. In addition to the methods on intervals, interval classes should implement:

  * `embed`
  * `intervaltype(T)`

`intervalclasstype(T)` and `ic` should be identities.
