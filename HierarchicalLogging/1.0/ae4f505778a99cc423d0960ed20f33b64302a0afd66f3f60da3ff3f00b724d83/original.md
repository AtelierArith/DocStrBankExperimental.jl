```
closest_registered_logger(h::HierarchicalLogger{T}, key) -> T
```

If `haskey(h, key)`, returns the logger associated with `key`.

Otherwise, returns the logger `L ∈ h` whose asssociated key `K` satisfies `startswith(key, K)` and the key of `L` is of maximal length among all such loggers in `h`.
