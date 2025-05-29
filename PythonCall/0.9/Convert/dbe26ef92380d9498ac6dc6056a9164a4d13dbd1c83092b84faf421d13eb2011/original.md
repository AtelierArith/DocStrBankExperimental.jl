```
@pyconvert(T, x, [onfail])
```

Convert the Python object `x` to a `T`.

On failure, evaluates to `onfail`, which defaults to `return pyconvert_unconverted()` (mainly useful for writing conversion rules).
