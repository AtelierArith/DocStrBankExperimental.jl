```
write_history(path::String,h::OptimiserHistory;ranks=nothing)
```

Write the contents of an `OptimiserHistory` object to a `path`. Provide MPI `ranks` when running in parallel.
