```
sumfinite([f=identity], A; kwargs...)
```

Compute `sum(f, A)` while ignoring any non-finite values.

The supported `kwargs` are those of `sum(f, A; kwargs...)`.
