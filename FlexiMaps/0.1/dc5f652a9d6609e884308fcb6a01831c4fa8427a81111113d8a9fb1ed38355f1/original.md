```
mapview(f, X)
```

Like `map(f, X)` but doesn't materialize the result and returns a view.

Works on arrays, dicts, and arbitrary iterables. Passes `length`, `keys` and others directly to the parent. Does its best to determine the resulting `eltype` without evaluating `f`. Supports both getting and setting values (through `Accessors.jl`).
