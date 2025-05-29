```
isinplace(ds::DynamicalSystem) → true/false
```

Return `true` if the dynamic rule of `ds` is in-place, i.e., a function mutating the state in place. If `true`, the state is typically `Array`, if `false`, the state is typically `SVector`. A front-end user will most likely not care about this information, but a developer may care.
