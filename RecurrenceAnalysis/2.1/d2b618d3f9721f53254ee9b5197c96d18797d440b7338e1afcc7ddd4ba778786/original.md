```
windowed(rmat, f, width, step = 1; kwargs...)
```

A convenience function that applies the RQA function `f`, such as `determinism`, to windowed views of the given recurrence matrix `rmat` with given window `width` and `step`. The `kwargs...` are propagated to the call `f(rmat_view; kwargs...)`.
