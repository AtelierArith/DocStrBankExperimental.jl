```
getresult(job::AbstractJob)
```

Get the running result of the `job`.

The result is wrapped by a `Some` type. Use `something` to retrieve its value. If it is `nothing`, the `job` is not finished.
