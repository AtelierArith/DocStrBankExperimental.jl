```
f64(x)
```

Change precision of `x` to `Float64`. It uses `Functors.fmap` to recursively traverse the fields of the struct `x`. For custom structs (e.g. `<:BlochSimulator` or `<:AbstractTrajectory`), it is required that `typeof(x)` be made a `Functors.@functor` (e.g. `@functor FISP`).

It may be necessary to add new adapt rules (by adding new methods to `adapt_storage`) if new structs with complicated nested fields are introduced.
