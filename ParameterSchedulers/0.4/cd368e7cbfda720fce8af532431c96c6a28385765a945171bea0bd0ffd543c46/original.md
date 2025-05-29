```
ComposedSchedule([(s, ps) -> T(ps...),] schedule::T, parameters)
```

A `schedule` whose fields are given by `parameters.(t)` at iteration `t`.

At each step `t`, this gets a new set of parameters with `parameters.(t)`, then creates a new `schedule` given the first (optional) argument. The new `schedule(t)` is the returned value.
