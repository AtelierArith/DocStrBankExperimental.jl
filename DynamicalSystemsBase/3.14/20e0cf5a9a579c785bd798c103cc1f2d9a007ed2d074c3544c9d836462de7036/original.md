```
isdeterministic(ds::DynamicalSystem) → true/false
```

Return `true` if `ds` is deterministic, i.e., the dynamic rule contains no randomness. This is information deduced from the type of `ds`.
