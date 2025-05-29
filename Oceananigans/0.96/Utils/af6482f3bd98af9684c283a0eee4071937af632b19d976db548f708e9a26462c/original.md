```
SpecifiedTimes(times)
```

Return a callable `TimeInterval` that "actuates" (schedules output or callback execution) whenever the model's clock equals the specified values in `times`. For example,

  * `SpecifiedTimes([1, 15.3])` actuates when `model.clock.time` is `1` and `15.3`.

!!! info "Sorting specified times"
    The specified `times` need not be ordered as the `SpecifiedTimes` constructor will check and order them in ascending order if needed.

