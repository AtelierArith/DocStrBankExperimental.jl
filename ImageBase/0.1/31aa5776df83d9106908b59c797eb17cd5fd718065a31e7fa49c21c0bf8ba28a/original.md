```
meanfinite([f=identity], A; kwargs...)
```

Compute `mean(f, A)` while ignoring any non-finite values.

The supported `kwargs` are those of `sum(f, A; kwargs...)`.
